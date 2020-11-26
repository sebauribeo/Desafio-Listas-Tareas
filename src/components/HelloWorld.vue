<template>
  <div class="container">
    <h1>Agrega Una Nueva Tarea</h1>
    <div class="dates">
      <input type="text" class="input" placeholder="Ingresa un Nombre" aria-label="nombre" aria-describedby="button-addon2" v-model="nombre">
      <div class="input-group-append">
        <button class="button" type="button" @click="mostrarNombre">Agregar</button>
      </div>
    </div>
    <section class="box" v-show="listaNombres.length > 0">
      <div class="box-2">
        <ul class="box_ul" v-for="(nombre,index) in listaNombres" :key="index">
          <li>{{nombre}}</li>
          <button type="button" class="button_2 btn btn-danger btn-sm" @click="eliminarNombre(index)">Eliminar</button>
        </ul>
      </div>
    </section>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data() {
        return {
            nombre: '',
            listaNombres: []
        }
    },
    methods: {
        mostrarNombre(){
            if (this.nombre) {
                this.listaNombres.push(this.nombre);
                this.nombre = "";
            } else {
                console.log("no tiene nombre");
            }
        },
        eliminarNombre(index){
            this.listaNombres.splice(index,1);
        }
    },
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style >
body {
  margin: 0;
  padding: 0;
  border: 0;
  background: #1d1d1d;
}
.box {
  width: 100%;
  display: flex;
  justify-content: center;
}
.box-2 {
    position: relative;
    margin: 50px;
    width: 400px;
    height: auto;
    background: linear-gradient(0deg, #000000, #262626);
    color: white;
}
.box-2:before, .box-2:after{
    content: '';
    position: absolute;
    top: -2px;
    left: -2px;
    background: linear-gradient(60deg, #fb0094, #0000ff, #00ff00, #fff000, #ff0000,#fb0094, #0000ff, #00ff00, #fff000, #ff0000);
    background-size: 200%;
    width: calc(100% + 4px);
    height: calc(100% + 4px);
    z-index: -1;
    animation: animate1 20s linear infinite;
}
.box-2:after{
filter: blur(20px);
}
@keyframes animate1{
    0%{
        background-position: 0 0;
    }
    50%{
        background-position: 600% 0;
    }
    100%{
        background-position: 0 0;
    }
}
ul li{
  text-align: justify;
  font-weight: 50px;
}
h1 {
  color: red;
}
.input {
  width: 200px;
  height: 50px;
  border-radius: 10px;
  text-align: center;
}
.button {
  margin: 30px;
  width: 100px;
  height: 50px;
  border-radius: 10px;
  background: grey;
  border: 3px solid red;
}
.box_ul {
  display: inline-flex;
  align-items: center;
}
.button_2 {
  width: 80px;
  height: 30px;
  border-radius: 10px;
  background: grey;
  border: 3px solid red;
  margin-left: 20px;
}
</style>

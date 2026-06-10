<template>

  <div id="app">
     <h1 class="title">{{title}}</h1>
    
     <div class="todo">

      <div class="input_box">
        <input class="input_item" type="text" v-model="todo" placeholder="Введите задачу...">
        <button class="input_btn" @click="addTodo(id++)">Добавить</button>
      </div>

      <div class="todo_list" v-for="(todo, i) in todos" :key="todo.id">
        <p class="todo_list_item" @dblclick="removeTodo(i)"> 
          <div>
            <span class="todo_id">{{ i + 1 }}. </span>
              <span 
              class="todo_text" 
              :class="{ todo_text_isShow: todo.isComplete }">
              {{ todo.text }}
            </span>
          </div>
                <span class="transparent" :class="{task_isDone: todo.isComplete}">Выполнено</span>
          <div>
            <input v-model="todo.isComplete" type="checkbox" class="todo_check">
          </div>

      </p>
      </div>
      <hr>
      <p class="total_count">Общее количество дел: {{ todos.length }}</p>
      
    </div>
  </div>

</template>

<script>
  export default {
    data() {
      return{
        title: "Список дел",
        todo: "",
        todos: [],
        isDone: false,
        id: 0
      };
    },
    methods: {
      addTodo(){
        this.todos.push({
          id: this.id,
          text: this.todo,
          isComplete: this.isDone
        })
        this.todo = "";
      },
      removeTodo(index){
        this.todos.splice(index, 1)
      }
    }

  };
</script>



<style lang="scss">
  // #app{
  //   display: flex;
  // }

  .transparent{
    color: red;
    display: none;
  }
  .task_isDone{
    display: flex;
  }

  .title{
    text-align: center;
    color: #7b7979;
  }
  .todo{
    width: 80%;
    max-width: 800px;
    height: 100%;
    background: rgb(232, 246, 251);
    padding: 30px;
    margin: 30px;
    outline: 1px solid rgb(188, 182, 182);
    border-radius: 10px;
    min-height: 400px;

    &_id, &_text{
      color: rgb(29, 239, 60);
      font-weight: bold;
      margin-right: 10px;
    }

    &_text_isShow{
        color: red;
        text-decoration: line-through;
      }

    &_check{
      display: inline-block;
    }
  }

.input_box {
  display: flex;
  width: 100%;
  margin: 20px 0;
}
/* стили для input */
.input_item {
  margin-right: 10px;
  width: 100%;
  height: calc(2.25rem + 2px);
  padding: 0.375rem 0.75rem;
  font-family: inherit;
  font-size: 1rem;
  font-weight: 400;
  line-height: 1.5;
  color: #212529;
  background-color: #fff;
  background-clip: padding-box;
  border: 1px solid #bdbdbd;
  border-radius: 0.25rem;
  transition: border-color 0.15s ease-in-out, box-shadow 0.15s ease-in-out;
}
.input_btn{
  border: 1px solid #d9d7d7;
  border-radius: 0.25rem;
  padding: 0.375rem 0.75rem;
  font-size: 1rem;
  font-weight: 400;
  line-height: 1.5;
  color: #212529;
  background-color: #e3dfdf;
}

.todo_list {
list-style: none;
padding: 0;
}
.todo_list_item {
  display: flex;
  justify-content: space-between;
  font-family: "Trebuchet MS", "Lucida Sans";
  padding: 7px 20px;
  margin-bottom: 10px;
  border-radius: 5px;
  border-left: 10px solid #f05d22; 
  box-shadow: 2px -2px 5px 0 rgba(0,0,0,.1),
      -2px -2px 5px 0 rgba(0,0,0,.1),
      2px 2px 5px 0 rgba(0,0,0,.1),
      -2px 2px 5px 0 rgba(0,0,0,.1);
  font-size: 16px;
  letter-spacing: 2px;
  transition: 0.3s all linear;
}
.todo_list_item:nth-child(2){border-color: #8bc63e;}
.todo_list_item:nth-child(3){border-color: #fcba30;}
.todo_list_item:nth-child(4){border-color: #1ccfc9;}
.todo_list_item:nth-child(5){border-color: #493224;}
.todo_list_item:hover {border-left: 10px solid transparent;}
.todo_list_item:nth-child(1):hover {border-right: 10px solid #f05d22;}
.todo_list_item:nth-child(2):hover {border-right: 10px solid #8bc63e;}
.todo_list_item:nth-child(3):hover {border-right: 10px solid #fcba30;}
.todo_list_item:nth-child(4):hover {border-right: 10px solid #1ccfc9;}
.todo_list_item:nth-child(5):hover {border-right: 10px solid #493224;}

.todo_check{
  text-align: right;
  width: 15px;
  height: 15px;
}
.total_count{
  color: rgb(18, 40, 234);
  font-weight: bold;
  font-size: 20px;
}


</style>

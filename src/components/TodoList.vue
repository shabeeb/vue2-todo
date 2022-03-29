<template>
  <div class="hello">
    <section class="vh-100" style="background-color: #eee">
      <div class="container py-5 h-100">
        <div class="row d-flex justify-content-center align-items-center h-100">
          <div class="col col-lg-9 col-xl-7">
            <div class="card rounded-3">
              <div class="card-body p-4">
                <div>
                  <a
                    href="http://shabeebk.com/blog/simple-vue-2-example-todo-list/"
                    target="_sb"
                    class="link"
                    >Read Full Blog
                  </a>
                </div>
                <h4 class="text-center my-3 pb-3">Simple Vue 2 To Do App</h4>

                <form
                  class="row row-cols-lg-auto g-3 justify-content-center align-items-center mb-4 pb-2"
                  @submit.prevent="addToDo"
                >
                  <div class="col-12">
                    <div class="form-outline">
                      <input
                        type="text"
                        id="form1"
                        v-model="newTodo"
                        class="form-control"
                        placeholder="Enter a task here"
                      />
                    </div>
                  </div>

                  <div class="col-12">
                    <button
                      type="button"
                      class="btn btn-primary"
                      @click="addToDo"
                    >
                      Save
                    </button>
                  </div>

                  <div class="col-12">
                    <button type="submit" class="btn btn-warning">
                      Get tasks
                    </button>
                  </div>
                </form>

                <table class="table mb-4">
                  <thead>
                    <tr>
                      <th scope="col">No.</th>
                      <th scope="col">Todo item</th>
                      <th scope="col">Status</th>
                      <th scope="col">Actions</th>
                    </tr>
                  </thead>

                  <tbody>
                    <tr
                      v-for="(todo, idx) in todos"
                      :key="todo.id"
                      :class="todo.completed && 'stricked'"
                    >
                      <th scope="row">{{ idx + 1 }}</th>
                      <td>{{ todo.title }}</td>
                      <td>
                        {{ todo.completed ? "Completed" : "In progress" }}
                      </td>
                      <td>
                        <button
                          type="submit"
                          class="btn btn-danger"
                          @click="removeItem(todo)"
                        >
                          Delete
                        </button>
                        <button
                          type="submit"
                          class="btn btn-success ms-1"
                          @click="toggleCompleted(todo)"
                        >
                          {{ todo.completed ? "Re-open" : "Complete" }}
                        </button>
                      </td>
                    </tr>
                  </tbody>
                </table>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
export default {
  name: "TodoList",
  props: {
    msg: String,
  },
  data() {
    return {
      newTodo: "",
      todos: [
        {
          id: 1,
          title: "Buy groceries for next week",
          completed: false,
        },
        {
          id: 2,
          title: "Pay credit card bill ",
          completed: false,
        },
      ],
    };
  },
  methods: {
    addToDo(e) {
      e.preventDefault();
      this.todos.push({
        id: this.todos.length + 1,
        title: this.newTodo,
        completed: false,
      });
      this.newTodo = "";
    },
    toggleCompleted: function (item) {
      item.completed = !item.completed;
    },
    removeItem: function (item) {
      this.todos = this.todos.filter((newItem) => newItem.id !== item.id);
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #37dd92;
}
a.link {
  color: #3771dd;
}
.stricked {
  text-decoration: line-through;
}
</style>

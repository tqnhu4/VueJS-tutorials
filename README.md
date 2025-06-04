# VueJS-tutorials
# 🌱 7-Day Vue.js Learning Roadmap for Beginners

Welcome to your accelerated Vue.js learning journey! This roadmap is designed to guide absolute beginners through the fundamentals of Vue.js within seven days, emphasizing practical application and rapid skill acquisition.

Each day focuses on a distinct set of core Vue.js concepts, complete with illustrative examples and a culminating practical project to solidify your understanding.
---

## 📅 Day 1: Vue.js Basics & Setup

Today, you'll set up your Vue.js environment and dive into the fundamental concepts of how Vue works.

### Content:
- **What is Vue.js?:** Understanding what Vue.js is, its benefits (progressive adoption, reactivity, component-based), and why it's a great choice for web development.
- **Installation & Setup:**
  - CDN (Content Delivery Network): The quickest way to get started for simple projects.
  - Vue CLI (Command Line Interface): For more robust projects. Learn how to install Node.js (if not already), then install Vue CLI and create your first project.
- **Vue Instance (new Vue()):** The heart of a Vue application.
  - el option (element to mount the Vue app to).
  - data option (reactive data for your application).
- **Template Syntax:**
  - Text Interpolation: Using {{ ... }} to display data.
  - Directives: Basic directives like v-bind (shorthand :) for binding attributes and v-text for updating element's text content.

---

### ✅ Example Code: Basic Vue App via CDN

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Day 1: Vue Basics</title>
  <script src="https://cdn.jsdelivr.net/npm/vue@2.6.14/dist/vue.js"></script>
</head>
<body>

  <div id="app">
    <h1>{{ message }}</h1>
    <p v-text="greeting"></p>
    <p>Your name: <span v-text="userName"></span></p>
    <a :href="vueLink">Learn Vue.js</a>
  </div>

  <script>
    new Vue({
      el: '#app',
      data: {
        message: 'Welcome to Vue.js!',
        greeting: 'This is a basic Vue application.',
        userName: 'Alice',
        vueLink: 'https://vuejs.org'
      }
    });
  </script>

</body>
</html>
```

---

## 📅 Day 2: Data Binding & Event Handling
Today, you'll learn how to make your application interactive by handling user input and responding to events.

### Content:
- **Two-Way Data Binding (v-model):** Easily bind form input values to your Vue instance data, creating a seamless connection.
- **Event Handling (v-on / @):**
  - Attaching event listeners (e.g., @click, @input, @submit).
  - Calling methods directly.
  - Event modifiers (e.g., .prevent, .stop).
- **Methods:** Functions defined within the Vue instance to encapsulate logic.

### ✅ Example Code: Basic Vue App via CDN

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Day 2: Data Binding & Events</title>
    <script src="https://cdn.jsdelivr.net/npm/vue@2.6.14/dist/vue.js"></script>
</head>
<body>

    <div id="app">
        <h2>Counter: {{ counter }}</h2>
        <button @click="increment">Increment</button>
        <button @click="decrement">Decrement</button>
        <button @click="reset(0)">Reset</button>

        <hr>

        <h2>Your Message:</h2>
        <input type="text" v-model="myMessage" placeholder="Type something...">
        <p>Echo: {{ myMessage }}</p>

        <hr>

        <form @submit.prevent="submitForm">
            <label for="nameInput">Name:</label>
            <input type="text" id="nameInput" v-model="formName">
            <button type="submit">Submit</button>
        </form>
        <p v-if="submittedName">Submitted Name: {{ submittedName }}</p>
    </div>

    <script>
        new Vue({
            el: '#app',
            data: {
                counter: 0,
                myMessage: '',
                formName: '',
                submittedName: ''
            },
            methods: {
                increment: function() {
                    this.counter++;
                },
                decrement: function() {
                    this.counter--;
                },
                reset: function(value) {
                    this.counter = value;
                },
                submitForm: function() {
                    this.submittedName = this.formName;
                    this.formName = ''; // Clear input after submission
                    alert('Form submitted with name: ' + this.submittedName);
                }
            }
        });
    </script>

</body>
</html>
```

---

## 📅 Day 3: Conditional Rendering & List Rendering
Today, you'll learn how to dynamically show/hide elements and render lists of data.

### Content:
- **Conditional Rendering:**
  - v-if / v-else-if / v-else: Conditionally render elements based on a condition. Elements are fully added/removed from the DOM.
  - v-show: Conditionally display elements by toggling their CSS display property. Elements remain in the DOM.
- **List Rendering (v-for):**
  - Iterating over arrays and objects to render multiple elements.
  - Using key attribute with v-for (essential for performance and state management).

### ✅ Example Code: 

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Day 3: Conditional & List Rendering</title>
    <script src="https://cdn.jsdelivr.net/npm/vue@2.6.14/dist/vue.js"></script>
</head>
<body>

    <div id="app">
        <h2>Conditional Rendering</h2>
        <button @click="toggleVisibility">Toggle Message</button>
        <p v-if="isVisible">This message is shown with v-if!</p>
        <p v-else>This message is shown with v-else!</p>

        <button @click="toggleDisplay">Toggle Display</button>
        <p v-show="isDisplayed">This message is shown with v-show!</p>

        <hr>

        <h2>List Rendering (Groceries)</h2>
        <ul>
            <li v-for="(item, index) in groceries" :key="index">
                {{ index + 1 }}. {{ item.name }} ({{ item.quantity }})
            </li>
        </ul>

        <h2>User List (Objects)</h2>
        <ul>
            <li v-for="(user, userId) in users" :key="userId">
                ID: {{ userId }} - Name: {{ user.name }}, Age: {{ user.age }}
            </li>
        </ul>
    </div>

    <script>
        new Vue({
            el: '#app',
            data: {
                isVisible: true,
                isDisplayed: true,
                groceries: [
                    { name: 'Milk', quantity: 1 },
                    { name: 'Bread', quantity: 2 },
                    { name: 'Eggs', quantity: 12 }
                ],
                users: {
                    'u001': { name: 'Bob', age: 28 },
                    'u002': { name: 'Carol', age: 35 },
                    'u003': { name: 'David', age: 22 }
                }
            },
            methods: {
                toggleVisibility: function() {
                    this.isVisible = !this.isVisible;
                },
                toggleDisplay: function() {
                    this.isDisplayed = !this.isDisplayed;
                }
            }
        });
    </script>

</body>
</html>
```

## 📅 Day 4: Computed Properties & Watchers
Today, you'll discover more advanced ways to handle data manipulation and reactions within your components.


### Content:
- **Computed Properties (computed):**
  - Calculated properties that depend on other data properties. They are cached based on their dependencies.
  - Useful for complex calculations or transforming data that is displayed in the template.
- **Watchers (watch):**
  - Observe changes in specific data properties and execute a function in response.
  - Useful for asynchronous operations or expensive operations that don't need to be run on every re-render.

### Example:
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Day 4: Computed & Watchers</title>
    <script src="https://cdn.jsdelivr.net/npm/vue@2.6.14/dist/vue.js"></script>
</head>
<body>

    <div id="app">
        <h2>Computed Property Example</h2>
        <input type="text" v-model="firstName" placeholder="First Name">
        <input type="text" v-model="lastName" placeholder="Last Name">
        <p>Full Name (Computed): {{ fullName }}</p>

        <hr>

        <h2>Watcher Example</h2>
        <p>Question: {{ question }}</p>
        <input v-model="question" placeholder="Ask a yes/no question...">
        <p>Answer: {{ answer }}</p>
    </div>

    <script>
        new Vue({
            el: '#app',
            data: {
                firstName: '',
                lastName: '',
                question: '',
                answer: 'I cannot give you an answer until you ask a question!'
            },
            computed: {
                // A computed property that combines firstName and lastName
                fullName: function() {
                    console.log('Computed fullName ran'); // Check when it runs
                    return this.firstName + ' ' + this.lastName;
                }
            },
            watch: {
                // Watch for changes in the 'question' data property
                question: function(newQuestion, oldQuestion) {
                    this.answer = 'Waiting for you to stop typing...';
                    this.getAnswer();
                }
            },
            methods: {
                // Simulate an API call to get an answer
                getAnswer: function() {
                    if (this.question.indexOf('?') === -1) {
                        this.answer = 'Questions usually contain a question mark. ;-)'
                        return
                    }
                    this.answer = 'Thinking...'
                    var vm = this
                    // Simulate an API call with setTimeout
                    setTimeout(function() {
                        if (Math.random() > 0.5) {
                            vm.answer = 'Yes'
                        } else {
                            vm.answer = 'No'
                        }
                    }, 500); // Simulate network delay
                }
            }
        });
    </script>

</body>
</html>
```  


## 📅 Day 5: Components - The Building Blocks
Today, you'll learn about components, the most powerful and flexible feature of Vue.js for building modular UIs.

### Content:
- **Why Components?:** Reusability, maintainability, and organization.
- **Defining and Registering Components:**
  - Global Registration: Using Vue.component().
  - Local Registration: Defining components within a parent component's options.
- **Props (Properties):** Passing data from a parent component to a child component.
  - Declaring props (props: ['propName'] or with validation).
- **Custom Events ($emit):** Communicating from a child component back to its parent.
### Example:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Day 5: Components</title>
    <script src="https://cdn.jsdelivr.net/npm/vue@2.6.14/dist/vue.js"></script>
</head>
<body>

    <div id="app">
        <h2>My App with Components</h2>
        <p>Total likes: {{ totalLikes }}</p>

        <my-button
            button-text="Like Post 1"
            @button-clicked="incrementTotalLikes"
        ></my-button>

        <my-button
            button-text="Like Post 2"
            @button-clicked="incrementTotalLikes"
        ></my-button>

        <product-card
            product-name="Laptop"
            :price="1200"
            image-url="https://via.placeholder.com/150/FF0000/FFFFFF?text=Laptop"
        ></product-card>

        <product-card
            product-name="Mouse"
            :price="25"
            image-url="https://via.placeholder.com/150/0000FF/FFFFFF?text=Mouse"
        ></product-card>
    </div>

    <script>
        // 1. Define a global component
        Vue.component('my-button', {
            // Props to receive data from parent
            props: ['buttonText'],
            template: `
                <button @click="handleClick">{{ buttonText }}</button>
            `,
            methods: {
                handleClick: function() {
                    // Emit a custom event to the parent
                    this.$emit('button-clicked');
                }
            }
        });

        // 2. Define a local component
        var ProductCard = {
            props: {
                productName: String,
                price: Number,
                imageUrl: String
            },
            template: `
                <div class="product-card">
                    <img :src="imageUrl" alt="Product Image" style="width:100px; height:auto;">
                    <h3>{{ productName }}</h3>
                    <p>Price: \${{ price }}</p>
                    <button>Add to Cart</button>
                </div>
            `
        };

        new Vue({
            el: '#app',
            data: {
                totalLikes: 0
            },
            // Register local components
            components: {
                'product-card': ProductCard
            },
            methods: {
                incrementTotalLikes: function() {
                    this.totalLikes++;
                }
            }
        });
    </script>

    <style>
        .product-card {
            border: 1px solid #ccc;
            padding: 10px;
            margin: 10px;
            display: inline-block;
            vertical-align: top;
            text-align: center;
        }
    </style>

</body>
</html>
```

## 📅 Day 6: Lifecycle Hooks & Routing (Basic)
Today, you'll understand the component lifecycle and how to manage different views in a single-page application.

### Content:
- **Component Lifecycle Hooks:**
  - Functions that are called at specific stages of a component's life (creation, mounting, updating, destruction).
  - Common hooks: created(), mounted(), updated(), destroyed().
- **Vue Router (Basic):**
  - Introduction to client-side routing for Single Page Applications (SPAs).
  - Installation and basic setup (Vue.use(VueRouter)).
  - Defining routes, <router-link>, and <router-view>.
  - **Note:** For this day, using Vue CLI will be more practical to demonstrate routing. If you're sticking to CDN, you can focus more on lifecycle hooks.

### Example (Vue CLI project structure assumed for routing):
If you're using Vue CLI, your main.js and component files would look something like this.
For CDN users, focus on the lifecycle hooks part in a single HTML file.

public/index.html (no changes needed from previous days)

src/main.js:

```javascript
import Vue from 'vue'
import App from './App.vue'
import VueRouter from 'vue-router' // Import Vue Router

Vue.config.productionTip = false

Vue.use(VueRouter) // Use Vue Router

// 1. Define Route Components
const Home = { template: '<div><h2>Home Page</h2><p>Welcome to the home page!</p></div>' }
const About = { template: '<div><h2>About Page</h2><p>Learn more about our app.</p></div>' }
const Contact = { template: '<div><h2>Contact Page</h2><p>Get in touch with us!</p></div>' }

// 2. Define Routes
const routes = [
  { path: '/', component: Home },
  { path: '/about', component: About },
  { path: '/contact', component: Contact },
]

// 3. Create the Router instance
const router = new VueRouter({
  routes // short for `routes: routes`
})

new Vue({
  router, // Mount the router to the Vue instance
  render: h => h(App),
}).$mount('#app')
```

src/App.vue:

```vue
<template>
  <div id="app">
    <h1>Vue App with Routing & Lifecycle Demo</h1>
    <nav>
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link> |
      <router-link to="/contact">Contact</router-link>
    </nav>
    <hr>
    <router-view></router-view>

    <hr>
    <LifecycleDemo />
  </div>
</template>

<script>
import LifecycleDemo from './components/LifecycleDemo.vue';

export default {
  name: 'App',
  components: {
    LifecycleDemo
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
nav a {
  margin: 0 10px;
  text-decoration: none;
  color: #42b983;
  font-weight: bold;
}
</style>
```

src/components/LifecycleDemo.vue (New Component):

```vue
<template>
  <div class="lifecycle-demo">
    <h3>Lifecycle Hooks Demo</h3>
    <p>{{ message }}</p>
    <button @click="message = 'Message Updated!'">Update Message</button>
  </div>
</template>

<script>
export default {
  name: 'LifecycleDemo',
  data() {
    return {
      message: 'Initial Message'
    }
  },
  beforeCreate() {
    console.log('beforeCreate: Component instance created, but data/methods not yet available.', this.message);
  },
  created() {
    console.log('created: Component instance created, data/methods now available.', this.message);
  },
  beforeMount() {
    console.log('beforeMount: Template compilation/rendering about to start.');
  },
  mounted() {
    console.log('mounted: Component mounted to the DOM. You can now access DOM elements.');
  },
  beforeUpdate() {
    console.log('beforeUpdate: Data changed, about to re-render.');
  },
  updated() {
    console.log('updated: Component re-rendered after data change.');
  },
  beforeDestroy() { // In Vue 3, this is `beforeUnmount`
    console.log('beforeDestroy: Component about to be destroyed.');
  },
  destroyed() { // In Vue 3, this is `unmounted`
    console.log('destroyed: Component destroyed and removed from DOM.');
  }
}
</script>

<style scoped>
.lifecycle-demo {
  border: 1px dashed #42b983;
  padding: 20px;
  margin-top: 30px;
}
</style>
```

## 📅 Day 7: Small Practical Project: Simple Todo List
Today is about consolidating your knowledge by building a small, practical Vue.js application.

### Content:
- **Building a Simple Todo List Application:**
  - **Features:** Add new todos, list existing todos, mark todos as complete, delete todos.
  - **Concepts applied:**
    - Vue Instance & data
    - v-model for input binding
    - v-on for event handling (add, delete, toggle complete)
    - v-for for list rendering
    - Conditional rendering (v-if or v-show) for styling completed tasks or showing "No tasks" message.
    - Methods for all logic.
### Example Project:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Day 7: Simple Todo List</title>
    <script src="https://cdn.jsdelivr.net/npm/vue@2.6.14/dist/vue.js"></script>
    <style>
        body { font-family: Arial, sans-serif; margin: 20px; background-color: #f4f4f4; }
        #app {
            max-width: 600px;
            margin: 30px auto;
            background-color: #fff;
            padding: 25px;
            border-radius: 8px;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
        }
        h1 { text-align: center; color: #333; }
        .add-todo { display: flex; margin-bottom: 20px; }
        .add-todo input { flex-grow: 1; padding: 10px; border: 1px solid #ddd; border-radius: 4px; }
        .add-todo button {
            padding: 10px 15px;
            background-color: #4CAF50;
            color: white;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            margin-left: 10px;
        }
        .todo-list ul { list-style: none; padding: 0; }
        .todo-item {
            display: flex;
            align-items: center;
            padding: 10px 0;
            border-bottom: 1px solid #eee;
            color: #555;
        }
        .todo-item:last-child { border-bottom: none; }
        .todo-item.completed span { text-decoration: line-through; color: #aaa; }
        .todo-item input[type="checkbox"] { margin-right: 10px; cursor: pointer; }
        .todo-item span { flex-grow: 1; }
        .todo-item button {
            background-color: #f44336;
            color: white;
            border: none;
            padding: 5px 10px;
            border-radius: 4px;
            cursor: pointer;
            margin-left: 10px;
        }
    </style>
</head>
<body>

    <div id="app">
        <h1>My Todo List</h1>

        <div class="add-todo">
            <input type="text" v-model="newTodoText" @keyup.enter="addTodo" placeholder="Add a new task...">
            <button @click="addTodo">Add Task</button>
        </div>

        <div class="todo-list">
            <p v-if="todos.length === 0">No tasks yet. Add some above!</p>
            <ul>
                <li v-for="todo in todos" :key="todo.id" class="todo-item" :class="{ completed: todo.completed }">
                    <input type="checkbox" v-model="todo.completed">
                    <span>{{ todo.text }}</span>
                    <button @click="removeTodo(todo.id)">Delete</button>
                </li>
            </ul>
        </div>
    </div>

    <script>
        new Vue({
            el: '#app',
            data: {
                newTodoText: '',
                todos: [],
                nextTodoId: 0
            },
            methods: {
                addTodo: function() {
                    if (this.newTodoText.trim() === '') {
                        return; // Don't add empty todos
                    }
                    this.todos.push({
                        id: this.nextTodoId++,
                        text: this.newTodoText.trim(),
                        completed: false
                    });
                    this.newTodoText = ''; // Clear the input field
                },
                removeTodo: function(id) {
                    this.todos = this.todos.filter(todo => todo.id !== id);
                }
            }
        });
    </script>

</body>
</html>
```

## 💡 Tips for Quick Learning and Immediate Application:
- **Hands-on Practice is Key!** The best way to learn Vue.js is by building. Try every example, then modify it, or build something similar on your own.
- **Start Simple:** Don't jump into complex features like Vuex or advanced routing until you're comfortable with the basics.
- **Understand Reactivity:** A core concept in Vue is reactivity. When you change data in your data object, Vue automatically updates the DOM.
- **Inspect with Vue Devtools:** If you're using Chrome or Firefox, install the Vue.js Devtools extension. It's incredibly helpful for debugging and understanding your component hierarchy and data.
- **Official Documentation is Gold:** Vue's documentation is exceptionally clear and comprehensive. Use it as your primary reference.
- **Community and Resources:** Join Vue.js communities on platforms like Reddit (r/vuejs), Discord, or Stack Overflow. There are also many great blogs and tutorials online.
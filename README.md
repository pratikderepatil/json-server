# Deploy `json-server` to `{{ free hosting site }}`

> Instructions how to deploy the full fake REST API [json-server](https://github.com/typicode/json-server) to various free hosting sites. Should only be used in development purpose but can act as a simpler database for smaller applications.

- [**Create your database**](#create-your-database)
- [Deploy to **Render**](#deploy-to-render)

## Create your database

1. Press the green `Use this template`-button in the right corner
2. Give your new repo a name and press the green `Create repository from template`-button
3. Clone your newly created repository to your computer

4 . Change the contents of `db.json` to **your own content** according to the [`json-server example`](https://github.com/typicode/json-server#example) and then `commit` your changes to git locally.

_this example will create `/posts` route , each resource will have `id`, `title` and `content`. `id` will auto increment!_

```json
{
	"posts": [
		{
			"id": 0,
			"title": "First post!",
			"content": "My first content!"
		}
	]
}
```

---

## Deploy to **Render**

<img align="right" width="100px" height="auto" src="https://dashboard.render.com/static/media/logo-redesign-02-word-dark.0811da26fe4b1f9a9b6c642d91bbcf73.svg" alt="Render">

The Render Public API is a REST API that lets you manage all of your Render services and resources through simple HTTP requests. With this API, you can have all the power of the Render dashboard through your own scripts, allowing you to integrate seamlessly with Render through your own scripts. _git_.

###### Pros

- Easy setup
- Free

### Deployment

1 . Create an account on <br/>[https://render.com](https://render.com)

2 . New > Web Service

3 . Used https://github.com/pratikderepatil/json-server repo.

4 . Added a Build Command of npm install

5 . Added a Start Command of npm start

The deploy was successful.

#### How it works

Render will look for a startup-script, this is by default `npm start` so make sure you have that in your `package.json` (assuming your script is called `server.js`):

```json
 "scripts": {
    "start" : "node server.js"
 }
```

You also have to make changes to the port, you can't hardcode a dev-port. But you can reference render port. So the code will have the following:

```js
const port = process.env.PORT || 3000;
```

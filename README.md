# Shopify Morning Bytes

## Setup a development store

- Sign up for a Shopify developer account at: `https://developers.shopify.com/`
- On the partner dashboard go to **Development stores** and click on **Create store**
- Enter details like your store name, address, and login info
- Login to your newly created store and add a new private app. This private app is how the build tools will be able to push code to your store.
  - Once logged in to your newly created store, go to **Apps** on the sidebar. Then click **Manage private apps**
  ![Private Apps](/images/private-app.png)
  - Click **Create a new private app**
  - Make sure to give the app read and write permissions for theme templates and theme assets
  ![App Permission](/images/private-app-permissions.png)
  - On the app's detail page copy the API password. This password will be put in an environment variable in the Slate build tool.
  - Go to **Online Store > Preferences** and disable password protection. Doing this makes the store public.

## Seed the store

Now that we have a store we need some stuff to sell.
- Download [apparel.csv](/import/apparel.csv)
- Go to **Products** and click on import to upload the csv file

## Getting started

Install node dependencies:
```
$ npm install
```

Create a `.env` file and put in the following environment variables:

| ENV Variable | Description | Example |
| --- | --- | --- |
| `SLATE_STORE` | The domain name for the store | `pat-morning-bytes.myshopify.com` |
| `SLATE_PASSWORD` | The API password for the private app | `1049e214b9c682b77be91ae087d59427` |
| `SLATE_THEME` | Theme ID or `live` for currently published theme | `61050060864` |

Example `.env` file:

```
SLATE_STORE=pat-morning-bytes.myshopify.com
SLATE_PASSWORD=1050e214b9c682b77be91ae087d59427
SLATE_THEME_ID=61050060864
```

With the environment setup, let's deploy our theme!

```
$ npm run deploy
```

After the theme is deployed we can start a watch for automatic uploading.

```
$ npm run watch
```

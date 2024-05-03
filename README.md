### How-to-Deploy-a-React-Website-on-cPanel-Without-Reloading-Issues

# Deploying a React Website on cPanel Without Reloading Issues

Many developers face challenges when deploying React websites on cPanel and encounter reloading issues in live sites. Follow these steps to deploy your React website smoothly.

## 1. Prepare Your React Project

- Build your React project using npm or yarn.
- Ensure that your project is optimized for production.

## 2. Set Up Your cPanel Account

- Log in to your cPanel account.
- Create a subdomain or add-on domain for your React website.

## 3. Prepare Folder

- Delete everything from your public_html folder.
- Create a ZIP file of your build/dist folder, or zip all the files inside the build/dist folder.

## 4. Deployment

- Upload your zip file into public_html. If using a subdomain, upload it to the corresponding folder.
- Extract the zip file, and move all files to the main folder (public_html or subdomain folder). Upload all files from your build/dist folder.

## 5. Solve Reload Issue

- Add a file to your main folder named ".htaccess".
- Add the following lines to the ".htaccess" file:

```
<IfModule mod_rewrite.c>
  RewriteEngine On
  RewriteBase /
  RewriteRule ^index\.html$ - [L]
  RewriteCond %{REQUEST_FILENAME} !-f
  RewriteCond %{REQUEST_FILENAME} !-d
  RewriteCond %{REQUEST_FILENAME} !-l
  RewriteRule . /index.html [L]
</IfModule>
```
### Now go to your live site and reload from any route, your site will work perfectly.

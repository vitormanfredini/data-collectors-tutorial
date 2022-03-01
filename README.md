# Don't Call It Cookies

## A tutorial on how to add a ~~Cookie~~ Data Collector Consent bar/popup to your website.

This tutorial uses [a lightweight & gdpr compliant cookie consent plugin written in plain javascript](https://github.com/orestbida/cookieconsent).

![Screenshot](https://github.com/vitormanfredini/data-collectors-tutorial/blob/main/screenshot.jpg?raw=true)

Here's how you do it:

1. Download these 2 files: `consent-config.js` and `consent.css`.

2. Upload `consent.css` to your server.

3. In `consent-config.js`:

  * Edit the line `theme_css: 'css/consent.css',` to point to the css file you just uploaded.

  * In this portion: `<a class="cc-link" href="#privacypolicypage">privacy policy</a>`, replace the `#privacypolicypage` with a link to your privacy policy page.

  * In this portion: `<a class="cc-link" href="#yourcontactpage">contact us</a>`, replace the `#yourcontactpage` with a link to your contact page.

4. Upload `consent-config.js` to your server.

5. Include the library and your configuration as follows:

```
<script src="https://cdn.jsdelivr.net/gh/orestbida/cookieconsent@v2.8.0/dist/cookieconsent.js"></script>
<script src="path-to-your-js-folder/consent-config.js"></script>
```
Don't forget to edit the `path-to-your-js-folder` portion with the correct path on your server.

6. Now we tell the library which script tags it should manage and what category they fit into.

  * Edit the attribute `type="text/javascript"` portion to read `type="text/plain"` on every script that collects data, so it doesn't load right away.

  * Add another attribute to specify its category: `data-cookiecategory="ads"`
Possible values are: `necessary`, `ads` and `analytics`.

Here's an example of what it should look like:

```
<script type="text/plain" data-cookiecategory="analytics" src="https://www.googletagmanager.com/gtag/js?id=UA-123456789-1"></script>
<script type="text/plain" data-cookiecategory="analytics">
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());

  gtag('config', 'UA-123456789-1');
</script>
```

7. That's it! You should now see the consent screen appearing on your website.

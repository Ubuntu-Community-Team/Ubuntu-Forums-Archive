---
title: "problems with subdomains"
date: 2012-06-09
forum: General Help
---

### Post by Skevil on 2012-06-09
I installed ubuntu desktop 12.04 on my server.
I tried to create a subdomain but if in the browser I type [*http://subdomain.localhost/index.html*](*http://subdomain.localhost/index.html*) I get: "404 - Not Found"

In "etc/hosts" I added: 127.0.0.2 subdomain.localhost
Then I created a file called "subdomain" in "/etc/apache2/sites-available/" and I wrote in it:

<VirtualHost *>
ServerName subdomain.localhost
DocumentRoot /home/name/400
</VirtualHost>

Then in the terminal I wrote: *sudo a2ensite subdomain* and *sudo /etc/init.d/apache2 restart*

What do I wrong?

ps. I apologize for my English, but I'm Italian.

---


---
title: "htaccess proxy"
date: 2009-09-17
forum: General Help
---

### Post by mridang on 2009-09-17
Hi Guys,

I have apache2 installed on my Ubuntu. I got the webserver up and running and it looks great. The default root for the webserver is /var/www. I have a subfolder here called ajaxterm. So basically to access it I'm typing [www.hostname.tld/ajaxterm/](www.hostname.tld/ajaxterm/) which serves me content from the /var/www/ajaxterm directory.

I have an application called Ajaxterm — it's a shell terminal in your browser — running on my machine on port 8200 which serves web pages as well. I'd like to create a .htaccess file in my /ajaxterm folder that serves me content from the sever running on port 8200. I think I'll have to use the apache mod_proxy or something. I'd like to make this transparent to the user. So when you're on [www.hostname.tld/ajaxterm](www.hostname.tld/ajaxterm) you're basically getting content served from the server on port 8200.

Does anyone know how i can do this?

Thanks in advance guys.

---


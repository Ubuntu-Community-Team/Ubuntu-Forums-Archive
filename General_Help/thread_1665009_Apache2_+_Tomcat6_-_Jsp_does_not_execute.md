---
title: "Apache2 + Tomcat6 - Jsp does not execute"
date: 2011-01-11
forum: General Help
---

### Post by unix_user on 2011-01-11
Please Let me know if this is not the right place to post.
I am trying to setup Ubuntu with Apache2+Tomcat6. I can get the site up and running, however when I have a jsp file
it does not execute, instead it just prints the full jsp to browser.

I am checking if there is a configuration issue that may be missed.

sudo /etc/init.d/tomcat6 status # shows fine

/etc/apache2/sites-available has a file for my site containing valid DocumentRoot

/home/user/sitename/webapps/examples
/home/user/sitename/webapps/examples/jsp
/home/user/sitename/webapps/examples/jsp/sample.jsp contains below text
<%= "hello" %>

When above page is visited in browser, it shows full html tags instead of displaying the output.
It displays static pages fine.

Let me know if I need to post more details.

Any help is appreciated,
Thanks,

---

### Post by hawkmage on 2011-01-11
Do you have eithr mod_jk or mod_proxy_ajp installed in Apache to send requests to Tomcat?  Normily the home for Tomcat is /vat/lib/tomcat6, did you change the CATALINA_BASE directory to point to your location?

---


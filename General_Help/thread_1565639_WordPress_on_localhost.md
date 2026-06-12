---
title: "WordPress on localhost"
date: 2010-09-01
forum: General Help
---

### Post by khatkarrohit on 2010-09-01
I have installed wordpress successfully.But i encountered a problem. When I access it locally it does not login instead it **shows the router logi**n page to me.

default settings were:
WordPress address (URL): [http://localhost](http://localhost)
Site address (URL) : [http://localhost](http://localhost)

with these settings it works fine, but with these settings the links become like this for rest of world:
[http://localhost/wp-content/themes/twentyten/images/headers/path.jpg](http://localhost/wp-content/themes/twentyten/images/headers/path.jpg)

so this image is not shown up in other people computers.
But it should be
[http://www.domain.com/wp-content/themes/twentyten/images/headers/path.jpg](http://www.domain.com/wp-content/themes/twentyten/images/headers/path.jpg)
to display correctly the image.

Then I changed the settings in Wordpress:
WordPress address (URL): [http://domain.com](http://domain.com)
Site address (URL) : [http://domain.com](http://domain.com)

But with these settings rest of world can access blog finely but when I access localhost it shows the router login page as domain.com resolves to router external IP address.

I have to use proxy to post anything on blog.

Please help out from this situation.
I want to access my blog locally too so that I dont have to use proxy to post new content.

---

### Post by khatkarrohit on 2010-09-07
I solved it by my self by Editing /etc/hosts and adding this entry to /etc/hosts.
127.0.0.1	rohitkhatkar.com

now I can access my site without using localhost directly typing name of my site.

---


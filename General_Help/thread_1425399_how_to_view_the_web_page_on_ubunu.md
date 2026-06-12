---
title: "how to view the web page on ubunu"
date: 2010-03-09
forum: General Help
---

### Post by C.mind on 2010-03-09
I have already installed apache2 and would like to view a simple page on the server but I don't how. which folder I should move the page to.

---

### Post by richardjh on 2010-03-09
Assuming you haven't changed anything the document root of the files, is 

/var/www/

There is by default a file called index.html which contains "It Works!" or something similar.

To view this in a browser go to [http://localhost/](http://localhost/)

That just shows apache is ready and working.

You can then put your site in /var/www if you are just using this locally or for testing or playing.

By default you wont have access to write to /var/www. You will need to set permissions accordingly or copy files in there using sudo.

---


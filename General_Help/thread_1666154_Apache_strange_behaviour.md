---
title: "Apache strange behaviour"
date: 2011-01-13
forum: General Help
---

### Post by Wtower on 2011-01-13
Hi,

On an intranet Ubuntu server running apache2 with the default document root (/var/www), I removed this particular directory and uploaded another instead. The previous directory had only an index.html file and no .htaccess or any other file. The new one has got several others along with an index.html as well. For some very peculiar reason, when I request the default document for that server with any browser (eg [http://server/](http://server/)), it makes the browser download a file to folder instead of presenting it. That file, containing the standard 'It works!' message, comes with a random file name of the type: sTNp8DKB.~.part . When I request a any specific file (eg [http://server/index.html](http://server/index.html)), it provides it as should. Any ideas?

---

### Post by Wtower on 2011-01-13
I tried to restart the apache2 service but for some reason it couldn't start. So I rebooted the machine and after that all fine. I got no idea what was that about, spent half a day googling.

---


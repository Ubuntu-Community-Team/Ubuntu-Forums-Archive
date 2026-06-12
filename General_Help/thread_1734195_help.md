---
title: "help"
date: 2011-04-20
forum: General Help
---

### Post by pouloton on 2011-04-20
hello
I have installed XAMPP in Ubuntu, but I do not know how the process continue after the start XAMPP. please guid:confused:

---

### Post by pouloton on 2011-04-20
Forgot to say.I want to install maker forum. But I do not know these steps to do after running XAMPP.
MyBB

---

### Post by Horseboy on 2011-04-21
Once you install it and do
```
/opt/lampp/lampp start
```you should be able to go to [http://localhost](http://localhost) in Firefox. I've made a video on YouTube if you're interested, [http://www.youtube.com/watch?v=XKlu-sy60_A](http://www.youtube.com/watch?v=XKlu-sy60_A)

And just about the user below's guide, yeah, I forgot to add you must chmod. Do
```
sudo chmod -R 777 /opt/lampp/htdocs
``` and you should be up and running.

Hope this helps and that you get XAMPP up and running :)

And as for installing myBB, download the package from their site and place the extracted archive in /opt/lampp/htdocs/mybb. Then, if you haven't configured security settings for XAMPP, you should be able to go to [http://localhost/phpmyadmin](http://localhost/phpmyadmin). Once there, create a database called mybb. Once that has finished, go to [http://localhost/mybb](http://localhost/mybb) and follow the installation instructions. If you'd like further help don't be afraid to ask :)

---

### Post by dino99 on 2011-04-21
[http://freshtutorial.com/install-xamp-ubuntu/](http://freshtutorial.com/install-xamp-ubuntu/)

---


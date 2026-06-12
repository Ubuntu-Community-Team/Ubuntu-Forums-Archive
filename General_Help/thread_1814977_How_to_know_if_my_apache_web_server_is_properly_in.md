---
title: "How to know if my apache web server is properly installed?"
date: 2011-07-30
forum: General Help
---

### Post by dandeliondream on 2011-07-30
Hi,
 
I am using vmware player, operating system is ubuntu. I have just installed the apache httpd-2.2.19. I am using the manual method. ./configure, make, make install. No error message.
 
When i run ubuntu, it gets into the terminal. From here, how do I know if my apache web server is properly installed?

---

### Post by bodhi.zazen on 2011-07-30
First, why are you installing apache from source code rather then the repositories ?

If you did not get an error message, then it is "installed". Starting and configuring it is going to be another matter, more so if you installed from source as you will probably now need to configure apache and write an init script.

What how-to are you following ?

Why are you not using the official server guide ?

[https://help.ubuntu.com/10.04/serverguide/C/httpd.html](https://help.ubuntu.com/10.04/serverguide/C/httpd.html)

Or community documentation ?

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by tgalati4 on 2011-07-30
When you log into the webpage from another machine (or the same machine [http://localhost](http://localhost)) you get:

It Works!

---

### Post by dandeliondream on 2011-07-30
I know there is an easier method but i am not allowed to use.
:(
> **bodhi.zazen said:**
> First, why are you installing apache from source code rather then the repositories ?
 
If you did not get an error message, then it is "installed". Starting and configuring it is going to be another matter, more so if you installed from source as you will probably now need to configure apache and write an init script.
 
What how-to are you following ?
 
Why are you not using the official server guide ?
 
[https://help.ubuntu.com/10.04/serverguide/C/httpd.html](https://help.ubuntu.com/10.04/serverguide/C/httpd.html)
 
Or community documentation ?
 
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by zero2xiii on 2011-07-31
> I know there is an easier method but i am not allowed to use.

Why is this?


To setup apache I recommend webmin, using it myself. To start apache, you need to actualy run it from the terminal cant remember the command syntax out of my head (webmin does this for me).. But just type "apa" and tab out twice, its the second option (NOT apache)...

Installing from source is a mess, even for people that know what they are doing, install from the repro's, that sets up all the enviroment vars and all the do das... And then apache "just works".

Good luck though..

---

### Post by bodhi.zazen on 2011-07-31
> **dandeliondream said:**
> I know there is an easier method but i am not allowed to use.
:(

Well, it sounds as if you are either doing something you should not or this is somehow homework related, I am not sure, and so am going to close this thread.

If you are not going to use the Ubuntu methods, and are going to compile on your own, then please read the Apache documentation and use the Apache mailing list.

---


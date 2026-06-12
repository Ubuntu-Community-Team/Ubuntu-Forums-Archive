---
title: "how to install wine in ubuntu in the PC without internet connection."
date: 2012-04-23
forum: General Help
---

### Post by shreyas_patel21 on 2012-04-23
Hello all,

I want to install wine in ubuntu 11.10

but I have no internet connection in that PC.

I can download package of wine through somewhere and then install.

How to install it using package like tar.gz?

I am new to ubuntu so forgive me for any mistake

thank you..

---

### Post by Novus Anima on 2012-04-23
You can download the stable release of Wine (1.2) from WineHQ: [http://www.winehq.org/download/ubuntu](http://www.winehq.org/download/ubuntu). Once you've downloaded it, you can move it onto a USB and then move it into your computer that has Ubuntu. Follow the instructions on that page (you should jot them down on paper or print out the page) on your Ubuntu PC.

---

### Post by techsupport on 2012-04-23
> **shreyas_patel21 said:**
> Hello all,

I want to install wine in ubuntu 11.10

but I have no internet connection in that PC.

I can download package of wine through somewhere and then install.

How to install it using package like tar.gz?

I am new to ubuntu so forgive me for any mistake

thank you..

Welcome to Ubuntu! :) 

It would be better to get a WIFI card or plug your ethernet into a local community college library or university network temporarily to get that just right. There are more packages needed than just Wine to run Wine. It really depends on which Windows software you plan on using.  I would recommend playonlinux for ubuntu instead. Find some broadband you can tap into to use for an hour.  

Try using a walkthrough guide like this:

[http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)

It is somewhere down the list, but really easy to install.

---

### Post by growingneeds on 2012-04-23
WINE is a meta-package. This means that it really isn't a single file, but instead it is a collection of files. You might try APTonCD. It is promising. BUt... you best bet would be to somehow get internet for that PC even for a while and

```
sudo apt-get install wine
```

An Android phone or iPhone with 3G connection? Or a network adapter allowing you to connect to WiFi temporarily?

Good luck.

---

### Post by Mark Phelps on 2012-04-23
> **shreyas_patel21 said:**
> ... I want to install wine in ubuntu 11.10..

BEFORE you go to all that trouble, suggest you find somewhere with an Internet connection, go to the WineHQ site, and look up the windows apps and versions (or games and versions) you want to use.

Wine is NOT a miracle cure that suddenly runs anything "Windows" in Linux.  Some stuff works well; some hardly works at all; other stuff doesn't work.

Given your lack of Internet connection, it would be worth your while to find out how well your planned apps/games work before you start down this path.  Anything you search for that is NOT listed on the WineHQ application compatibility site is likely NOT to work; anything rated less than GOLD is going to be a waste of your time.

And finally, realize that anything you want to use in Wine will have to be INSTALLED.  So, if you have a dual-boot PC (running both MS Windows and Linux), you can't use Wine to run your existing Windows apps.  And, in many cases, if the Windows app is already installed and running on another PC, installing it on this PC is going to DEactivate it on the other PC.

Wine is not a miracle cure ...

---

### Post by shreyas_patel21 on 2012-04-26
> **Novus Anima said:**
> You can download the stable release of Wine (1.2) from WineHQ: [http://www.winehq.org/download/ubuntu](http://www.winehq.org/download/ubuntu). Once you've downloaded it, you can move it onto a USB and then move it into your computer that has Ubuntu. Follow the instructions on that page (you should jot them down on paper or print out the page) on your Ubuntu PC.

exactly I need the instructions required after getting wine pack from internet to install from the package..

thank you.

---

### Post by Mark Phelps on 2012-04-26
> **shreyas_patel21 said:**
> exactly I need the instructions required after getting wine pack from internet to install from the package..

thank you.

Reread post #4 -- it's NOT that simple.  

The reason you need to add the ppa is that attempting to install the Wine package will cause the installer to go out (using the Internet) to the repositories, search for, find, and download OTHER packages.

You would have to use the apt-get approach and download ALL the packages needed -- not just Wine.

---

### Post by shreyas_patel21 on 2012-04-29
> **Mark Phelps said:**
> Reread post #4 -- it's NOT that simple.  

The reason you need to add the ppa is that attempting to install the Wine package will cause the installer to go out (using the Internet) to the repositories, search for, find, and download OTHER packages.

You would have to use the apt-get approach and download ALL the packages needed -- not just Wine.


thank you!

if I download all depended package then can i install it without internet?

---


---
title: "Customize boot screen"
date: 2011-09-29
forum: General Help
---

### Post by nine9nine on 2011-09-29
Hi, everyone.  I have Ubuntu 10.10 installed on my laptop, and I was wondering if I could change the boot animation.  Right now, for some reason, I don't have any animation, but I know that the default is "Ubuntu" and the loading dots.  I was wondering how to get the default back, since it doesn't show it, and how to change it to be a boot that I make myself.

---

### Post by ajgreeny on 2011-09-29
The "animation" is plymouth, and it is easy to change the plymouth theme that is used to one of the alternatives which you can find in synaptic.  The default is plymouth-theme-ubuntu-logo.

I am not sure if things have moved on, but it used to be impossible to remove plymouth from the machine without completely messing up the whole system; perhaps things have changed now, so search for **plymouth configuration** to see if it throws up any ideas.

---

### Post by Frogs Hair on 2011-09-29
If you have installed a proprietary graphics card driver this will  cause splash screen problems . I used the fix at the link and it is the only one that has worked for me .[http://www.omgubuntu.co.uk/2011/05/how-to-fix-the-plymouth-boot-screen-when-using-proprietary-graphics-drivers/](http://www.omgubuntu.co.uk/2011/05/how-to-fix-the-plymouth-boot-screen-when-using-proprietary-graphics-drivers/)

I have also installed the Zorin splash screen manager , and  there are plymouth  themes at Gnome Look . 

[http://gnome-look.org/content/show.php/Splash+Screen+Manager?content=134231](http://gnome-look.org/content/show.php/Splash+Screen+Manager?content=134231)

This is the animation I am currently using .[http://gnome-look.org/content/show.php/Ubuntu+sunrise+plymouth?content=129696](http://gnome-look.org/content/show.php/Ubuntu+sunrise+plymouth?content=129696)

---

### Post by nine9nine on 2011-09-30
But how can I create my own theme?

---

### Post by Frogs Hair on 2011-09-30
I have not looked into making my own themes . You may want to download a plymouth theme , extract the file , and see how they are put together .

---

### Post by seawolf167 on 2011-09-30
I believe [*burg*]("http://code.google.com/p/burg/") supports animated boot menus as well. How-to install [here]("https://help.ubuntu.com/community/Burg").

---


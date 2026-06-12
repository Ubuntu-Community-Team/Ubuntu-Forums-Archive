---
title: "how optimize ubuntu 11.04 to be faster"
date: 2011-08-17
forum: General Help
---

### Post by IT Support on 2011-08-17
Hi guys! 
I want advice! 
I have ubuntu 11.04  and i seems that it works slower than early 
ubuntu , i have running ubuntu classic but no matter it work slow :(
at first i had problem with wireless driver but i fix it, everything is working well now.  
I have old leptop:
fujitsu siemens amilo pro v8010  
CPU:Celerom M 1.3 Hgz
RAM:1.5Gb
with integrated VGA
can i get work  faster this ubuntu  or what edvice you can give me ?
or i will return early version of ubuntu ?

---

### Post by kerry_s on 2011-08-17
Try lubuntu.

---

### Post by IT Support on 2011-08-17
> **kerry_s said:**
> Try lubuntu.

I tryed it in future and it was slow in work too :( i had tryed  more debians   (ubuntu,kubuntu,lubuntu,ubuntu mint "Isadora" and others) but for me faster of them was ubuntu 10.10  then i upgrade  10.10 to 11.04  and after upgrade begin  problems  :) 
so i see it isnot solution for my old leptop and i shell downgrude 11.04 to 10.10 :(


by the way i dislike KDE menu  , can i install gnom menu in kubuntu ??

---

### Post by mastablasta on 2011-08-17
> **IT Support said:**
> I tryed it in future and it was slow in work too :( i had tryed more debians (ubuntu,kubuntu,lubuntu,ubuntu mint "Isadora" and others) but for me faster of them was ubuntu 10.10 then i upgrade 10.10 to 11.04 and after upgrade begin problems :) 
so i see it isnot solution for my old leptop and i shell downgrude 11.04 to 10.10 :(

 
are there any active processes slowing it all down? what graphics card do you use?
type
 
lspci 
 
in terminal to get the graphics card chip. 
 
>  
by the way i dislike KDE menu , can i install gnom menu in kubuntu ??
 
KDE menu? does that mean you are using Kubuntu? if so then first thing to do is turn off all special effects. also KDE is a bit more heavier on resources. you can install Gnome desktop and on reboot select which one you want to use. like this: [http://www.psychocats.net/ubuntu/gnome](http://www.psychocats.net/ubuntu/gnome)
 
GNOME is desktop environment not just menu. same goes for KDE.

---

### Post by kerry_s on 2011-08-17
> by the way i dislike KDE menu , can i install gnom menu in kubuntu ??

So your using kde, not gnome? Kde is the heaviest desktop. 
No you can not use gnome menu in kde.

---

### Post by IT Support on 2011-08-17
> **mastablasta said:**
> are there any active processes slowing it all down? what graphics card do you use?
type
 
lspci 
 
in terminal to get the graphics card chip. 
 

 
KDE menu? does that mean you are using Kubuntu? if so then first thing to do is turn off all special effects. also KDE is a bit more heavier on resources. you can install Gnome desktop and on reboot select which one you want to use. like this: [http://www.psychocats.net/ubuntu/gnome](http://www.psychocats.net/ubuntu/gnome)
 
GNOME is desktop environment not just menu. same goes for KDE.

i have this graphic card 
Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)


 I have ubuntu 11.04  not kubuntu , maybe i wrote  not correct , reason is my bad english  :)

i asked that if i will install kubuntu,  can i install gnom there too? 

and i get answer from kerry_s   that i can`t 

 :)

i think there isn`t more active processes  i  install new ubuntu  whith clear install yesterday

---

### Post by Duncan Williams on 2011-08-17
Usually the slow response and other stuff is related to a few things.
Video driver, window manager, 3D effects, OpenGL.

Using unity 2D is usually one way to speed things up.

The distro I am using is very fast even on limited/older computers
and is based on ubuntu 11.04. It uses one of the fastest desktops `LXDE'.

Peppermint:
[http://peppermintos.com/](http://peppermintos.com/)

It may well be worth trying this distro if it's easy enough for you to download.

---

### Post by kerry_s on 2011-08-17
> 
i asked that if i will install kubuntu, can i install gnom there too? 


i thought you wanted gnome menu as kde menu.

the desktop yes. you can install them all if you want to try. the thing is you won't get the speed if your installing on top of a already slow system. you need to try it all by itself, which is why i suggested lubuntu. it is made to be light & quick.
[http://lubuntu.net/](http://lubuntu.net/)

---

### Post by oldos2er on 2011-08-17
If Lubuntu was slow for you, I don't see how a heavier DE e.g. Gnome or KDE will be faster.

---

### Post by IT Support on 2011-08-17
Duncan Williams
kerry_s
oldos2er

thank you all guys i will try  both  lubuntu and peppermint too :)

---


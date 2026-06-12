---
title: "No GUI after updating to Ubuntu 9.10"
date: 2009-11-10
forum: General Help
---

### Post by Pesky_Programmer on 2009-11-10
I have recently began using Ubuntu and have been using 9.04 for the past few month with out too many problems. However I have recently upgraded to 9.10 and can no longer get to the graphical log in screen.
 
When Ubuntu finished upgrading to 9.10 it restarted. When it did Ubuntu displayed a white ubtuntu symbol in the center of the screen for a few moments and then began displaying text only to the screen. The text rapidly flickered for a minute and then stopped. I was then prompted to login and i did so using my old user name and password. However I cant seam to get to my desktop or any other graphical controls.
 
I would like to be able to get my desktop back so I can recover some of my files in my home folder. However i am prepared to download 9.10 ISO and do a fresh install I just would rather leave that as a last resort.
 
Here are my system specs if it will help any:
Gateway MX7527
ATI MOBILITY RADEON X600
Mobile AMD Athlon(tm) 64 Processor 4000+
 
Also I was running Jaunty 64 bit if that helps.

---

### Post by michy99 on 2009-11-10
After you log in, enter this in the terminal:```
startx
```If you get an error message, post it here.

---

### Post by Pesky_Programmer on 2009-11-10
OK i gave startx a try and it put a bunch of writing up on the screen but here is the error portion that i think you were looking for.
 
Fatal server error:
no screens found
 
Xinit: No such file or directory (errno2): unable to connect to x server
Xinit:No such process (errno3): sever error

---

### Post by michy99 on 2009-11-10
Here's something I found on another post:

Do the following in this order:

First login and type:```
sudo gdm
```If nothing:```
sudo /etc/init.d/gdm start
```Nothing still...

Finally, this will reset your xorg.conf to a default state:```
sudo dpkg-reconfigure -phigh xserver-xorg
```Restart afterwards.

---

### Post by bradleypariah on 2009-11-10
I had the same issue!

Not sure if this works for everyone, but boot off the Live CD.

Once there, open a terminal and type

```
gksudo nautilus
```Navigate your way to **/etc/ X11/ **

Once there, delete the file named **xorg.conf**

Take out the disk and reboot.

---

### Post by Pesky_Programmer on 2009-11-10
[FONT=Times New Roman][SIZE=3]I tried all of the commands you told me and non of them will work[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]> [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][FONT=Times New Roman][SIZE=3]Sudo gdm[/SIZE][/FONT][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Listed a pile of warning I will only post if you ask for them.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[COLOR=black][SIZE=3][FONT=Times New Roman]>  
[COLOR=black][SIZE=3][FONT=Times New Roman]sudo /etc/init.d/gdm start[/FONT][/SIZE][/COLOR]

[/FONT][/SIZE][/COLOR][COLOR=black][SIZE=3][FONT=Times New Roman] [/FONT][/SIZE][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]this causes the screen to flicker and I have to restart to fix it[/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3] [/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]>  
[COLOR=black][SIZE=3][FONT=Times New Roman]sudo dpkg-reconfigure -phigh xserver-xorg[/FONT][/SIZE][/COLOR]
[/FONT][/SIZE][/COLOR][COLOR=black][FONT=Times New Roman][SIZE=3] [/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]this seams to do nothing no errors or messages.[/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3] [/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3]Thanks for the help even though it does not seam to be working just yet.[/SIZE][/FONT][/COLOR]

---

### Post by Pesky_Programmer on 2009-11-10
[COLOR=black][FONT=Verdana]Maybe I should of said this before but I was unable to get 3d to work in 9.04 and used this to link to modify my xorg. Not sure if this lead to my currant problem.[/FONT][/COLOR]
 
[http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue](http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue)
 
Also I tried useing my live cd of 9.04 and I can now a[COLOR=black][FONT=Verdana]ccess Ubuntu files and back them up to my flash drive or into windows files. However the update used up a gig of my 5 gig monthly bandwidth so I will wait until i can download Karmic ISO and do a fresh install. Untill then I am open to any ideas on how to salvage my currant install if at all possible.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana][/FONT][/COLOR] 
[COLOR=black][FONT=Verdana]Again thanks for the help it is g[COLOR=black][FONT=Verdana]reatly appreciated.[/FONT][/COLOR][/FONT][/COLOR]

---

### Post by mjhacker on 2009-11-17
Could you post the contents of your xorg.conf file for us?

---

### Post by Pesky_Programmer on 2009-11-20
[COLOR=black][FONT=Verdana]Being so frustrated with the apparent inability for Ubuntu to have a proper updater I have since deleted that partition and all of its contents. I have also downloaded and installed Karmic with a fresh install.[/FONT][/COLOR]

---

### Post by Kralnor on 2009-11-21
> **bradleypariah said:**
> I had the same issue!

Not sure if this works for everyone, but boot off the Live CD.

Once there, open a terminal and type

```
gksudo nautilus
```Navigate your way to **/etc/ X11/ **

Once there, delete the file named **xorg.conf**

Take out the disk and reboot.

Yup, I had the same problem too. The Live CD wasn't even needed. All I had to do was cd into /etc/X11 and do rm xorg.conf.

---

### Post by Goggeli on 2009-11-21
If you want to save your files in the system, you can simply boot your computer from a live-cd and then mount your ubuntu disk, just copy all the needed files over to a usb-stick or an external hard-drive.

---

### Post by dff3bc on 2011-02-21
Do this:

cd to /etc/X11

sudo nano xorg.conf

change the resolution to a lower one

control+o

control+X

sudo reboot

---


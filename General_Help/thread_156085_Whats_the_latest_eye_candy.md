---
title: "Whats the latest eye candy?"
date: 2006-04-06
forum: General Help
---

### Post by veelivar on 2006-04-06
Hello,

I'm thinking of havinng a play with Ubuntu again (now I have a nvidia card..)

What i would like to know tough is what is the best way currently to make it look/work well (prefereabliy in gnome)?

I've had a look at some of poofyhairguy's excellent posts on the subject but I must admit to being a little lost as to what is current/best.  What I *think* I need to do is this:

upgrade to dapper
install latest nvidia drivers
use xgl
find a theme I like (any reccomendations something nice clean and slick? with wow! factor).

Is this correct/all?

And how difficult a job is this? 

I alwas had a problem with my windows tearing around the edges whne I dragged them around befor which really didn't look slick at all.  I'm hopeing that the new graphics card (6800 GS AGP) and the best eye candy will solve that?  I have actually noticed windows does it too actally.  I guess I just noticed it more in ubuntu...

Cheers,
Dan.

---

### Post by karthik085 on 2006-04-06
upgrading to dapper, installing nvidia drivers, xgl, compiz....depends on how comfortable you are with linux. I would say, it is pretty easy. If you are newbie, it might take little more time. 

Even though Dapper is in developmental version, it is close to beta stage and very stable. I have been using it for past 1-2 months. And every day, it gets better.

Besides, the list you mentioned, you can try different different 
desktop environemnts like KDE, XFCE...
window managers like Enlightenment17(E17), Enlightenment16(E16). fluxbox, ...E17 is one of the best, even thought it is still in development stage.
3ddesktop, if you have problems with Xgl or Compiz
different themes, icons, wallpaper, screensvaer, splash screens...

If you like GNome, I wrote a post on Customizing it:
[http://ubuntuforums.org/showthread.php?t=73427](http://ubuntuforums.org/showthread.php?t=73427)

Moreover, if you want to know more other than eye candy, like optimizing your system to the best performace, configuring xserver, applications, beagle search, mono, multimedia codecs, automatix, etc.....read the posts related to it on the forums

Check more at Howtos, Tips and Trucks, Gnome/Kde forums for Eye candy related threads.

---

### Post by funkenstein on 2006-04-06
1. latest dapper iso - [http://www.ubuntu.com/testing/flight6](http://www.ubuntu.com/testing/flight6)
2. extra repositories - [http://easylinux.info/wiki/Ubuntu_dapper](http://easylinux.info/wiki/Ubuntu_dapper)
3. ```
sudo apt get update; sudo apt-get upgrade
``` in your command line
4. NVidia drivers - [http://www.ubuntuforums.org/showthread.php?t=139264](http://www.ubuntuforums.org/showthread.php?t=139264) (try method 1, as those *are* the latest ones
5. go to gnome-look.org and get the icons/themes you like
6. XGL/Compiz [http://www.ubuntuforums.org/showthread.php?t=148351](http://www.ubuntuforums.org/showthread.php?t=148351)

Do it in that order. 

Files to backup as soon as you've finished setting it all up:
*/etc/fstab - manages your harddrives, cdroms and partitions. Useful if you want to have other harddrives/are using a dual-boot system
*/etc/apt/sources.list - manages the sources of all the extra software you can install. You want to keep a stock copy of this one
*/etc/X11/xorg.conf - controls your xserver - what lets you see more than white text on a black background. You need a pristine version of this at all times, just in case things get b0rked as you play around (experience talking here...) and don't just call it xorg.conf.backup or xorg.conf_backup, cuz it'll get overwritten. I like using ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.`date +%s`
``` the date +%s give you a unique number (seconds since 1970-01-01 00:00:00 UTC, so a new one every second) and makes sure its backedup uniquely!

NOTE:
a. xgl is experimental. Expect it to break, and hope it won't (use it and hope, it hasn't borked. yet.)
b. xgl/compiz has its own 'theme', the only thing you can change is the colour. The howto I followed is the one with the 'thefuture' script. I find that the theme manager breaks when you run it after the thefuture script. I therefore change the theme, then run thefuture. 

7. Have fun, play nice. :mrgreen:

---

### Post by veelivar on 2006-04-07
Thats excellent! thank you.  As soon as my neww router arrives I'll be ready to play....

Edit: This is probably a really daft question.  but which type of theme should I be looking at for the way that buttons, edges to windows, menus' etc look?

 GTK 1.x ?
 GTK 2.x ?
 Metacity ?
 GDM Themes ?

Dan.

---

### Post by veelivar on 2006-04-08
Soory to bump this but posts fly by so fast here that posts get lost easily.

Any chance any one knows the difference between the different themes?  

Cheers,
Dan.

---

### Post by dave9191 on 2006-04-08
GDM themes - What the login screen will look like. 
Metacity - what the window border and title bar will look like
GTK - the toolkit for drawing buttons, menu's, etc... Gnome uses GTK 2.x, 

--
Dave

---

### Post by veelivar on 2006-04-10
[QUOTE=dave9191]GDM themes - What the login screen will look like. 
Metacity - what the window border and title bar will look like
GTK - the toolkit for drawing buttons, menu's, etc... Gnome uses GTK 2.x, 

--
Dave[/QUOTE]

Thanks so basically I want to find a combination all 3 and icons that I like ?

Dan.

---

### Post by dave9191 on 2006-04-10
Basically yah :)

--
Dave

---

### Post by Paulus on 2006-04-10
Hey, does anyone know if e17 works with XGL/compiz?  I´m compiling e17 now to try and find out!

---

### Post by linuxfueled on 2006-04-10
How about this?

[IMG]http://linuxfueled.homelinux.com:8080/gallery2temp/ubuntugloworange.png[/IMG]

[http://linuxfueled.com]("http://linuxfueled.com")

---


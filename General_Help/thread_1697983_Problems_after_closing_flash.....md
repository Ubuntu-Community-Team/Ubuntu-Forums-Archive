---
title: "Problems after closing flash...."
date: 2011-03-01
forum: General Help
---

### Post by DachaArh on 2011-03-01
Hi all :) 

So, not matter is it Firefox or Opera.. I sometimes have problem after closing tab, in which I watched some flash video ( mostly youtube...
First specifinations :
GPU : MSI Nvidia GeForce 9500GT 512MB, 128 bit ( installed restricted drivers, latest version, recomended..)
Flash plugin is latest stable, Firefox and Opera too...
System : Ubuntu 10.10 gnome ( installed just few days ago, but it happened before to..)
Compiz enabled, latest stable...


So I open video in new tab... watch it ( sometimes whole, sometimes just part..) and sometimes, when I close that tab, I have problems with that part of screen, where that video was - system wide..
Some letter are not whole.. you can't read them... some colors are mixed, and wrong..

It looks like this :

[[IMG]http://i124.photobucket.com/albums/p31/DachaArh/Bezveze/th_1.jpg[/IMG]](http://i124.photobucket.com/albums/p31/DachaArh/Bezveze/1.jpg)

**I have to take picture with digital camera, since print screen points correct image, so that means that I have either monitor, or GPU problem.. ( No problem on Windows 7, and I think no problem with Compiz beta, but alot of other bugs with compiz beta :( )**

This is how it should look:

[[IMG]http://i124.photobucket.com/albums/p31/DachaArh/Bezveze/th_1true.jpg[/IMG]](http://i124.photobucket.com/albums/p31/DachaArh/Bezveze/1true.jpg)

When I opened those images on ubuntu, I wanted to crop them.. I noticed that some flash video, in background.. not the flash, but that last image frame only..
So how I move image viewer, that image stays in same place - that is the place where I have problem..
Here are images on that :

[[IMG]http://i124.photobucket.com/albums/p31/DachaArh/Bezveze/th_tube3.jpg[/IMG]](http://i124.photobucket.com/albums/p31/DachaArh/Bezveze/tube3.jpg)

[[IMG]http://i124.photobucket.com/albums/p31/DachaArh/Bezveze/th_tube2.jpg[/IMG]](http://i124.photobucket.com/albums/p31/DachaArh/Bezveze/tube2.jpg)


all images are thumbnails, click to view :) 

Please help me solve this :(

Edit:
I forgot

compiz --replace does not help..
I have compiz started with loose binding option, does that have something to do with this?

There is no way to correct this, expect restart.. Or editing screen resolution, then changing back...

---

### Post by turtle153 on 2011-03-01
Have you tried without the ATI proprietary drivers? I find the built-in Ubuntu ones are much better and more reliable.

---

### Post by DachaArh on 2011-03-01
It is Nvidia card, not ATI :)

And I can not have visual affects without restricted drivers :(

thanks for help, anyway.. ;)

I hope someone else had problem and solved..

I noticed that is only happens if I have embeeded flash on site, but window is smaller than youtube original, so I click on title of video, to open youtube in new tab...
After closing that tab... that embeeded flash crashes, and if that area, there are those visual problems, on whole system, browsers, text editors, image viewers.. :(

---

### Post by Ast0815 on 2011-03-09
I seem to have the same or at least a similar problem.

I couldn't find a reliable way to reproduce it yet, but sometimes, if I watch a flashvideo on a website, the last frame gets "burned" into the background of the system. meaning that all the areas that should be white (even those in the nautilus) show the last frame of the video instead.

I'm on Ubuntu 10.10, Firefox 3.6.15 and Shockwave Flash 10.2r152.
Oh, and I'm using the proprietary Nvidia drivers.

It's rather annoying, 'cause the only way to get my system back to normal (as far as I know at the moment) is to log out and log in again.

Any tips how I could fix or analyse this problem further are appreciated.

---

### Post by JeremyA on 2011-03-10
I'm having the same problem after upgrading to the latest proprietary nvidia drivers.  I run in a dual-screen setup, and if I start the browser in the left-hand monitor, watch some flash, and then close it, I can see the video "afterburn" in the left side.

If I then open the browser in the right-hand monitor, and watch more flash, the "afterburn" does not appear on the right-hand monitor--instead, it is _updated_ in the left hand monitor.

killing X has been my only method for getting rid of the after image.  It's annoying.

I've also noticed that the afterburn follows as I rotate the desktop cube, or move to additional workspaces -- it's always in the location it was when it started.

My first thought is to blame flash.

And I'd try the non-proprietary drivers, but I want the performance for WINE games :)

---

### Post by Owen.C93 on 2011-03-15
Same problem, except mine started crashing my whole OS. 1 quick black flash and then no movement of mouse or anything, pressing my power button will initiate shutdown and show a corrupted shutdown screen. After that I have to remove my battery from my laptop.

Happens after using flash 10.2 and 10.3.


EDIT: D'oh,I created a thread for this and there is a possible solution inside. [http://ubuntuforums.org/showthread.php?t=1684777](http://ubuntuforums.org/showthread.php?t=1684777)

I'm not sure if it works yet, still testing.

---

### Post by pqwoerituytrueiwoq on 2011-03-15
right click flash ->settings 
uncheck hardware acceleration and see if it helps
you can also try using html5 instead of flash for youtube
[http://www.youtube.com/html5](http://www.youtube.com/html5)

---


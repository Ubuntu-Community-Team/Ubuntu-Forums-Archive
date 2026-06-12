---
title: "How to set a wallpaper for the grub menu."
date: 2009-08-10
forum: General Help
---

### Post by Bearded-flower on 2009-08-10
Hey i was using mint a while back and it has a nice little feature, it has a wallpaper in the grub menu.

## sorry if i posted this in the wrong section, if so please move it, and im sorry if this has been anwered in another post, i searched to no avail.

---

### Post by mthalis on 2009-08-10
Use start up manager..
**sudo apt-get install startupmanager**

Read This
[http://www.ubuntugeek.com/startup-manager-change-settings-in-grub-grub2-and-usplash.html](http://www.ubuntugeek.com/startup-manager-change-settings-in-grub-grub2-and-usplash.html)

---

### Post by arky on 2009-08-10
[http://embraceubuntu.com/2006/03/21/add-a-grub-splash-image/](http://embraceubuntu.com/2006/03/21/add-a-grub-splash-image/)

---

### Post by Bearded-flower on 2009-08-11
No as in an image in the grub menu, not the loading screen, the grub menu (where you select your OS)

---

### Post by mthalis on 2009-08-11
I'm confuse,Can you explain it more? Did you try **startupmanager** I used that to set image to my grub.It works fine.

---

### Post by Bearded-flower on 2009-08-11
Yeah i did but i can only find how to edit your bootloader.

---

### Post by sonu 1807 on 2009-08-11
1. In boot options choose 24 bit as colour depth 
2. In Appearance select use colours in boot menu
3. Under Bootloader Themes select a grub image with .xpm extension (googling will give you some links to such images)
4. Select Use Background Image for bootloader menu

Then close

---

### Post by Bearded-flower on 2009-08-11
> **sonu 1807 said:**
> 1. In boot options choose 24 bit as colour depth 
2. In Appearance select use colours in boot menu
3. Under Bootloader Themes select a grub image with .xpm extension (googling will give you some links to such images)
4. Select Use Background Image for bootloader menu

Then close
But will that kill off my bootloader?

---

### Post by sonu 1807 on 2009-08-11
You have to install start-up manager and also you should have some .xpm grub images ...it won't kill your bootloader

---

### Post by Bearded-flower on 2009-08-14
Ok then, does anyone know where i can find an .xpm images?
i have only found about 6... all of which suck.

---

### Post by arky on 2009-08-15
Make yourself one 

[http://ubuntuforums.org/showthread.php?t=528442](http://ubuntuforums.org/showthread.php?t=528442)

---

### Post by Donalb on 2009-11-03
Pretty early for specific Karmic ones. I was using a nice Grub background on Intrepid until today's update.

Just looking for something nice after installing Karmic.


gnome-look.org is usually your best best for graphics stuff like this.That's where I'll start & where I got my last one. Like this:
[http://gnome-look.org/content/show.php/Tux+GRUB+Splash?content=36909](http://gnome-look.org/content/show.php/Tux+GRUB+Splash?content=36909)

Haivng more difficulty adding a background screen this time though.

---

### Post by ranch hand on 2009-11-03
Grub2 will use .png images just fine.  Both Gimp and Gthumb will convert any image you want to use.  If scaling is needed stick with gimp.

---

### Post by Bearded-flower on 2009-11-04
when does grub2 come out?

---

### Post by x C0MMAND0 x on 2009-11-04
Wow, startupmanager is an amazing program I have installed but have never used...Thanks!

---

### Post by x C0MMAND0 x on 2009-11-04
> **Bearded-flower said:**
> when does grub2 come out?

It is out and comes with Karmic i believe.

---

### Post by Bearded-flower on 2009-11-04
aaaaaah. stupid question.

---

### Post by x C0MMAND0 x on 2009-11-04
> **Bearded-flower said:**
> aaaaaah. stupid question.

Not a stupid question.  I just learned about Grub 2, 2 days ago when I began experimenting with it after I heard some features about it.

---

### Post by ranch hand on 2009-11-04
> **x C0MMAND0 x said:**
> Not a stupid question.  I just learned about Grub 2, 2 days ago when I began experimenting with it after I heard some features about it.
See the link in my sig.  The links are good ones.  The first three are great and the first one is probably the most complete, if hard to navigate.  His menu background stuff was way ahead of anyone else and real good.

You do not need to download the "grub2-splashimages", however.  It does, sometimes make it easier but that guide was written several versions ago.

Getting the size right on complex images is tricky.  Kind of bland or images with a lot of "unimportant" stuff around the outside are best.

It is FUN.

---

### Post by Bearded-flower on 2009-11-05
> **x C0MMAND0 x said:**
> Wow, startupmanager is an amazing program I have installed but have never used...Thanks!

Argh i have nightmares about startup manager.
It destoyed my boot. couldnt boot into ubuntu AND i missed the release of 9.10 :(

---

### Post by ranch hand on 2009-11-05
And it does not, at this point support grub2.  An update is coming.

I used it for a while.  I prefer to do it myself.

---

### Post by Bearded-flower on 2009-11-05
can anyone gimme a hand? [http://ubuntuforums.org/showthread.php?t=1315179](http://ubuntuforums.org/showthread.php?t=1315179)

---


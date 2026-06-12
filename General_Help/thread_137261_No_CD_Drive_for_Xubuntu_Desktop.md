---
title: "No CD Drive for Xubuntu Desktop?"
date: 2006-02-27
forum: General Help
---

### Post by fishmorg909 on 2006-02-27
I installed the Xubuntu desktop, and it's pretty good. But I just found that the CD Drive won't show up on the desktop -- not on screen, and not in the Desktop Folder. I thought I saw a thread concerning this problem, but my searches can't dig it up. How do I tune XFCE to show CD-ROMs?

(Another, smaller, problem -- the icon for 'hide all windows' disappeared from the top bar. Where'd that sucker go?)

---

### Post by 5-HT on 2006-02-27
Hi,

[quote=fishmorg909]But I just found that the CD Drive won't show up on the desktop -- not on screen, and not in the Desktop Folder. I thought I saw a thread concerning this problem, but my searches can't dig it up. How do I tune XFCE to show CD-ROMs. [/quote]

XFCE does not by default draw the desktop or automount removable media (two things which I love about it).

To mount a CD-ROM (you cannot mount an audio cd, just open up a player and point to it) you can either do it by:

i) XFCE menu > system > XFCE fstab mount manager

ii) via terminal:

```
 mount /media/cdrom0 
```

*The mount point will be different for different devices. The general form is:

mount <device> <mount point>. 

Read 'man mount' for all the details.

iii) Use gnome-volume-manager to automount removable media just like if you were using GNOME

[https://wiki.ubuntu.com//LowEndSystemSupport](https://wiki.ubuntu.com//LowEndSystemSupport)

----------

To browse the CD, simply point a filemanager or the terminal to 

```
 /media/cdrom0 
```, or other if appropriate.


-----------------------------

If you want to be able to have desktop icons, this thread may be of help:

[http://ubuntuforums.org/showthread.php?t=118917](http://ubuntuforums.org/showthread.php?t=118917)

-----------------------

[quote=fishmorg909] Another, smaller, problem -- the icon for 'hide all windows' disappeared from the top bar. Where'd that sucker go? [/quote]

Right click on end of panel > click "Add new item" > select "Show Desktop".



Hope that helps.

---

### Post by fishmorg909 on 2006-02-27
Okay, cool, using the xfce fstab mount mgr....

Here's another dumb question -- how do I get it to eject the disk? Duh? :confused:

---

### Post by fishmorg909 on 2006-02-28
Okay, running

> sudo eject

gets the CD out, but isn't there a way in Xfce fstab mounter? There doesn't seem to be an 'eject' button or menu. (And of course right-click > Eject doesn't work.)

---

### Post by 5-HT on 2006-02-28
[QUOTE=fishmorg909] There doesn't seem to be an 'eject' button or menu. (And of course right-click > Eject doesn't work.)[/QUOTE]


I haven't noticed any option to eject from the mount manager.
I just unmount the drive and eject it by pressing the button on the drive itself (once it's unmounted, the drive's no longer locked).

If you'd like to eject it with a command, what you were doing seems the best bet. Shouldn't need to use sudo though.

---

### Post by DigitalDuality on 2006-04-12
if this is all the case how well does cd-burning perform in xfce?

---

### Post by 5-HT on 2006-04-12
[quote=DigitalDuality]if this is all the case how well does cd-burning perform in xfce?[/quote] 
I haven't had any problems.
Just put the disc in, open up your favorite burning suite, and have at it!
There should be options in most suites that allow the disc to be ejected after burning, or you could just eject manually.

---


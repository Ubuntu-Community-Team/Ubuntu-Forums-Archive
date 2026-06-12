---
title: "Error The panel encountered a problem while loading &quot;OAFIID:DrapesApplet&quot;"
date: 2010-01-02
forum: General Help
---

### Post by Rytron on 2010-01-02
Hi.
I get this error in a window on startup: [in attached picture].

I reinstalled gnome-applets and gnome-applets-data in synaptic packet manager but the error still appears. I have uninstalled drapes. How do I solve this?

Thanks.

---

### Post by Endolith on 2010-03-22
It doesn't say "Delete" and "Don't delete"?

For me, all my applets fail to load after a first boot.  If I then log out and log back  in, it works.  I don't know why, but it happens every time.

---

### Post by wibinem on 2010-05-04
just try to remove panel folder.....
/home/<user>/.gconf/apps/panel/

try to login again....
:)

---

### Post by Endolith on 2010-05-04
That removes everything from the panel!

---

### Post by Endolith on 2010-05-08
And it **STILL** gives the error after a reboot.  I have to log back out and log back in again.  Such a useless OS.

---

### Post by Rytron on 2010-05-09
> **Endolith said:**
> And it **STILL** gives the error after a reboot.  I have to log back out and log back in again.  Such a useless OS.

Try this; reinstall gnome-applets and gnome-applets-data in synaptic.

**Ubuntu is an awesome OS. Give it a chance.**

---

### Post by Endolith on 2010-05-09
> **Rytron said:**
> Try this; reinstall gnome-applets and gnome-applets-data in synaptic.

I already did that in March.

**> Ubuntu is an awesome OS. Give it a chance.**I've given it several years of being my primary OS, and no, it's not awesome.  It's buggy, frustrating, and unreliable.

---

### Post by Rytron on 2010-05-10
Well Endolith, people differ. I used to use Windows. Initially when I crossed to Ubuntu 7.10 I found it to be a bit buggy (the wireless was tricky). However with each new release, I have found it to be an excellent OS.

---

### Post by Rytron on 2010-05-10
@ Endolith! Install Ubuntu 10.04. Then consider using Wallpaper Tray instead of Drapes. Remember that no OS is perfect. You may want to try Linux Mint also.

---

### Post by Endolith on 2010-05-10
> **Rytron said:**
> Well Endolith, people differ. I used to use  Windows. Initially when I crossed to Ubuntu 7.10 I found it to be a bit  buggy (the wireless was tricky). However with each new release, I have  found it to be an excellent OS.

That's fine, but it's the opposite of my experience.  I used to use Windows, and I switched to Ubuntu several years ago.  Initially when I crossed to Ubuntu, I was pleasantly surprised at how well it worked.  However, with each new release, I've experienced more and more bugs, regressions, and problems (like this one).  Now, I avoid upgrading for several months because my computer typically becomes unusable after the "upgrade", and it takes a week or two to get it back in working order.

> Then consider using Wallpaper Tray instead of Drapes.I don't have either of those.  I just have a plain black background for my desktop.  It's the applets that are crashing.

> Remember that no OS is perfect.No, but some are better than others.

---

### Post by Decon1986 on 2010-05-21
This is my first post ever, so here it goes.

Wallpaper-tray was one of my favorite apps on Ubuntu. I get tired of the  same desktop and load a new one every two minutes. I also switched from  Windows, but not entirely. True, there are bugs in Ubuntu, and I also  hate upgrading for the same reasons, that it often requires a whole new  setup. However, problem solving these bugs has made me more computer  savvy, and I often know more than anyone in the room (not a computer  science major). 

I saw this discussion and it helped me out the most:  [http://swiss.ubuntuforums.org/showthread.php?p=9121420](http://swiss.ubuntuforums.org/showthread.php?p=9121420)

Basically, you shouldn't run drapes if you're not changing your  wallpaper often. You can probably change this by going to System>  Preferences> Startup Application (in the later versions of Ubuntu, Sessions in the earlier versions).  Check off or delete the 'drapes' entry. 

If it's not there, and it's an  app that you added to the panel, try typing "sudo apt-get remove drapes" in a terminal. You can also push alt-f2, input the command into the box, and check off "Run in terminal."

Finally, if you updated to Lucid, wallpaper-tray did not work for me immediately. I installed "libboost-filesystem1.40.0" and "libboost-system1.40.0" through synaptic after downloading  "wallpaper-tray_0.4.6-5_i386.deb" from: [http://archive.ubuntu.com/ubuntu/pool/universe/w/wallpaper-tray/](http://archive.ubuntu.com/ubuntu/pool/universe/w/wallpaper-tray/)

Install libboost first, then install wallpaper-tray through gdebi package installer. Wallpaper-tray will run in the notification area, not as a panel app (as in later versions of wallpaper-tray). 

If anyone is going to say use drapes, I tried making it run at start-up in lucid and it failed after trying both methods of checking off the box in the app and manually adding it to startup. A google search showed this was a bug in earlier Ubuntu versions as well. I chose to fix good ol' wallpaper-tray instead.

---

### Post by Craigus on 2010-05-21
Thanks Decon, your solution worked fine for me on Mint 9, which is Lucid based...

---

### Post by hhall on 2010-05-24
I followed those instructions to install wallpaper tray. It appears to have installed, but how do I actually get it to start?

Thanks

---

### Post by Rytron on 2010-05-24
> **hhall said:**
> I followed those instructions to install wallpaper tray. It appears to have installed, but how do I actually get it to start?

Thanks

Add it to a panel.

---

### Post by hhall on 2010-05-24
How? It doesn't appear to offer me that option...

---

### Post by Rytron on 2010-05-25
> **hhall said:**
> How? It doesn't appear to offer me that option...

Right click on a panel. Then hit 'Add to Panel'. Scroll down and you will see 'Wallpaper Tray'. Select it and Add.

---

### Post by hhall on 2010-05-25
Yes, that would appear logical. But it does not appear on the scroll-down menu.

---

### Post by Rytron on 2010-05-25
> **hhall said:**
> Yes, that would appear logical. But it does not appear on the scroll-down menu.

Verify you have it installed!

```
sudo apt-get install wallpaper-tray
```

---

### Post by hhall on 2010-05-25
That appears to be the case: 

Quote:
wallpaper-tray is already the newest version.
The following packages were automatically installed and are no longer required:
  kdelibs4c2a firefox-3.5-branding kdelibs-data liblualib50 libavahi-qt3-1
  libgnomecanvasmm-2.6-1c2a libxml++2.6-2 libgnomemm-2.6-1c2 libqt3-mt
  libgnome-vfsmm-2.6-1c2a liblua50 libgnomeuimm-2.6-1c2a

But I can't see it in the drop-down...

---

### Post by Rytron on 2010-05-25
This is what I have! Does anyone else know how to help hhall?

---

### Post by MrEgg on 2010-05-29
I did get Drapes load on startup doing the following :
[LIST=1]
[*]In Drapes' Preferences / General tab, do not check Launch on startup
[*]In System / Preferences / Startup Apps, manually enter a new entry :
[INDENT]name : Wallpaper Drapes[/INDENT]
[INDENT]command : drapes --tray[/INDENT]
[/LIST]

Cheers,
Egg

---

### Post by MartijnNL on 2010-05-30
I'm using Jaunty and got the applet error as well.

Next I just ran "drapes" as a command instead and that works fine. Using "drapes --tray" got me an error message that the tray options doesn't exist, but just using "drapes" got it to run in the tray as well. For now I've kept "Launch on Startup" checked and I will see tomorrow if it works fine, otherwise I'll add it to Startup Applications.

---

### Post by Craigus on 2010-11-15
I can confirm that Decon1986's method also works with Mint 10, which is based on MM .

---

### Post by Craigus on 2011-05-27
I can also confirm that this still works for Linux Mint 11, which is NN based.

Note that you will have to add wallpaper-tray to startup applications.

---


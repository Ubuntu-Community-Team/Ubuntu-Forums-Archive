---
title: "My netbook has become unusable"
date: 2009-11-30
forum: General Help
---

### Post by james.exe on 2009-11-30
I installed 9.10 on my Acer Aspire One za3. Everything was running fine except the screen resolution which was the same deal back in jaunty. I browsed around the forums for a fix to the problem and came across this link
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo)
However, upon following "1" from "Karmic (9.10) - New Method", I went ahead and restarted my netbook for the changes to take effect. I see the ubuntu symbol shining in the center just like a regular start up and then all of a sudden, my screen starts flickering nonstop. Apparently, it won't load the GUI. I've tried recovery mode and it's the same exact thing except that the screen isn't flickering and I'm able to actually type stuff into my computer.
Any way I can get my computer up and running again? I've had so much bad luck with Ubuntu in the past that if this doesn't get solved, I'm seriously considering going back to windows.
Pretty please :/

---

### Post by Mutant Corn on 2009-11-30
You may need to just go back to an earlier version. This sort of thing happens sometimes...when Hardy came out, I lost all functionality of my intel wireless card, and no fixes were available.

---

### Post by Cope57 on 2009-11-30
[DreamLinux]("http://www.dreamlinux.com.br/")

---

### Post by james.exe on 2009-11-30
I mean according to the threads I've read, the screen resolution did in fact get fixed. My main issue now is getting the GUI to run again.
Right now my screen is all black with this white text that's similar to what's on the terminal so I'm guessing I can run commands from here to maybe reverse what I just did or fix my computer?

---

### Post by james.exe on 2009-11-30
Just to show how far I've attempted to look into the problem, I've tried
```
startx
```and
```
sudo /etc/init.d/gdm restart
```No success. 
Note: When I run startx, I noticed somewhere in the babble of code
** FATAL: Module psb not found**

Maybe that helps?
 I really do in fact need help and I'm not just being lazy like some people.

---

### Post by james.exe on 2009-11-30
Here's some other stuff that I think may be relevant.
When I run start x, I get:
```
FATAL: Module psb not found.
(EE) [drm] drmOpen failed.
(EE) PSB(0): [dri] DRIScreenInit failed. Disabling DRI.
(EE) [drm] Could not uninstall irq handler
(EE) PSB(8): This driver currently needs DRM to operate

Fatal server error:
AddScreen/ScreenInit failed for driver 0

Please consult the The X.Org Foundation support
at http://wiki.x.org
for help.
```

---

### Post by nothingspecial on 2009-11-30
[[COLOR="Magenta"]This[/COLOR]]("http://www.tipsandthoughts.com/?p=4") might help

---

### Post by james.exe on 2009-11-30
Again, I appreciate the thought, but I don't want to install a new OS. I have all my files on my netbook for school and do not wish to lose those. I just want to know how to get my GUI started again whether it's downgrading the OS or reversing the last code I ran to get my screen resolution corrected, which was:
```
wget http://gma500re.altervista.org/scripts/poulsbo_ppa.sh && sh ./poulsbo_ppa.sh
```

---

### Post by nothingspecial on 2009-11-30
James, I`m not suggesting you install a new operating system. 

If you read the link you will see that post contains instructions on how to install the missing psb module.

I have no idea weather it works or not but it`s worth a try.

---

### Post by nothingspecial on 2009-11-30
Another thought occurs to me, bearing in mind I`ve no idea what you`ve done.

I`m guessing you`ve compiled a module (driver) against your current kernel. Does grub give you the option of booting into a previous kernel?

If so you can boot into the previous kernel, remove the current one then reinstall it cleanly.

If you have no idea what I`m talking about, post back.

---

### Post by james.exe on 2009-11-30
Not too sure what you mean by grub. If grub is the menu that shows up when I press esc, this is what it's showing me:

```
Ubuntu 9.10, kernel 2.6.31-15-generic
Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode)
Ubuntu 9.10, kernel 2.6.31-14-generic
Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
Ubuntu 9.10, kernel 2.6.31-16-generic
Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)
Ubuntu 9.10, memtest86+
```I've tried all three recovery modes and when I resume normal boot, I get taken to the same black prompt screen. I also tried dpkg to see if maybe that'd do the trick, but nothing :/
I think I kinda see where you're going with the previous guide you linked me to. The only problem is that I'm not too knowledgeable when it comes to linux so idk how to do a lot from just the terminal alone; I've only been using ubuntu since august. Either way, I think those are the repositories that became obsolete with the coming of karmic. That's why I had to follow a new guide to get my resolution and video in order. What I'd also like to know is if theres a way to back up my files from the prompt screen and send it to my external or usb if all else fails.

---

### Post by Greenwidth on 2009-11-30
Do you have an xorg.conf in /etc/X11/ ?

Karmic does not need one anymore to setup display as it does it on the fly (if there is one present it will use its settings), so if you do have it, deleting it should make X start with 'default' settings.

Probably best to copy it to xorg.conf.backup so that you can replace it if needed.

From the recovery console check to see if xorg.conf exists:
```
ls /etc/X11/
```

if it does back it up:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

delete xorg.conf:
```
sudo rm /etc/X11/xorg.conf
```

Restart.

Hopefully you won't need to, but to reinstate xorg.conf:
```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```

---

### Post by james.exe on 2009-12-05
Sorry for the late reply, I've been busy. I tried making a backup xorg.conf, but for some reason it didn't let me so I just went ahead with the removing of it. That seems to have done the trick. You guys don't understand how grateful I am to not have to go through the hassle of wiping out my hard drive. My sincerest thanks!

---


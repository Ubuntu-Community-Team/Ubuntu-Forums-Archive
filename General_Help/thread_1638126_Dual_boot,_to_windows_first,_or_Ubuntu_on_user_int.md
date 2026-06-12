---
title: "Dual boot, to windows first, or Ubuntu on user interaction"
date: 2010-12-05
forum: General Help
---

### Post by BlackLab on 2010-12-05
How do I configure boot so that the computer boots straight into windows xp, unless I press a key during boot?

---

### Post by jroa on 2010-12-05
You will need to open a terminal and type **sudo gedit** /**boot**/**grub**/**menu**.**lst .  **Post a screen shot or just copy and paste that text in that file to this thread.  We can tell you what to change from there.

---

### Post by tredegar on 2010-12-05
> You will need to open a terminal and type **sudo gedit /boot/grub/menu.lst**
That file no longer exists with grub2

To change the boot order you need to do:
```
sudo grub-set-default [COLOR="Red"]X[/COLOR]
```
with [COLOR="Red"]X[/COLOR] being the menuentry position (starting with 0 as the first entry) of your windows boot.

More information is here: 
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by Mark Phelps on 2010-12-05
An "easier" way to do this is to install startup-manager.

Once that is installed, you will have a GUI app that will allow you to select the default OS/kernel launched using a pull-down.  That can be a lot less work than trying to figure out absolute OS/kernel stanza locations every time GRUB updates.

---

### Post by BlackLab on 2010-12-05
> **Mark Phelps said:**
> An "easier" way to do this is to install startup-manager.

Once that is installed, you will have a GUI app that will allow you to select the default OS/kernel launched using a pull-down.  That can be a lot less work than trying to figure out absolute OS/kernel stanza locations every time GRUB updates.

startup-manager sounds good if updates to GRUB are going to be a problem. I have not actually installed Ubuntu on the target computer yet.

Is startup-manager the name of a utility provided by Ubuntu?
When I install Ubuntu, what option do I need to choose regarding boot?

---

### Post by BlackLab on 2010-12-06
re: startup-manager

looking here: [https://help.ubuntu.com/community/StartUpManager#Running%20Start-UpManager]("https://help.ubuntu.com/community/StartUpManager")
and here: [https://help.ubuntu.com/community/StartUpManager#Security%20/%20Advanced](https://help.ubuntu.com/community/StartUpManager#Security%20/%20Advanced)


I don't see an option to press a key during boot to change the boot option.

---


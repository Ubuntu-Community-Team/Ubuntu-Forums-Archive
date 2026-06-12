---
title: "Global menu is loading in Gnome Shell"
date: 2011-10-13
forum: General Help
---

### Post by 8_Bit on 2011-10-13
I installed Oneiric, fresh install. Then installed Gnome Shell.

When I load it up, it appears that the Global menu from Unity is loading too. I see the File, Edit, etc all in the top, but garbled and mixed with the Gnome Shell menubar.

This only happens if I install the proprietary drivers for AMD (fglrx).

Additionally there is noticeable pixelation/garbled graphics throughout Gnome Shell after I install the drivers.

What is going on??

---

### Post by Vaphell on 2011-10-13
upgraded from 11.04 here. I get garbled mess on my 1215b (AMD fusion CPU+GPU) too. Half of characters is missing like 'L g ut. .' for 'Logout...' and such. Totally unusable.
Gnome classic fallback mode on the other hand seems quite ok, but it looks off when using the theme used by unity. Panel looks completely flat while panel indicators, clock and menus get that graphite gradient slightly 3d look from unity and stick out like a sore thumb. Does anyone know how to fix that?

---

### Post by 8_Bit on 2011-10-13
Thank you for replying, glad to know I'm not the only one experiencing this.

I wonder somehow if it has anything to do with this.
[http://www.sabayon.org/article/gnome-3-shell-and-fglrx-fixed-next-driver](http://www.sabayon.org/article/gnome-3-shell-and-fglrx-fixed-next-driver)
[https://bugzilla.gnome.org/show_bug.cgi?id=652029](https://bugzilla.gnome.org/show_bug.cgi?id=652029)
[https://bugzilla.novell.com/show_bug.cgi?id=685691](https://bugzilla.novell.com/show_bug.cgi?id=685691)

This is basically what I get on my screen. Garbled mess on the top. All sorts of random colors, and the Unity Global Menu text overlayed on top of it. And if I click on it repeatedly enough, I can actually open the File/Edit menus for a split second.
[img]http://s0.i1.picplzthumbs.com/upload/img/2d/5a/02/2d5a0247e02ba4449749ef5ad7e37da505063514_wmlg.jpg[/img]

I checked in the activity monitor. There's absolutely no Unity process running.

This is a disappointment. I absolutely need the proprietary drivers for my work since I'm a 3D modeler and I need full 3D hardware acceleration for Blender.
Hope the devs know about it and are at least looking at it. I might have to use Gnome Fallback in the meantime I guess.

---

### Post by BazookaAce on 2011-10-13
> **8_Bit said:**
> I installed Oneiric, fresh install. Then installed Gnome Shell.

When I load it up, it appears that the Global menu from Unity is loading too. **I see the File, Edit, etc all in the top**, but garbled and mixed with the Gnome Shell menubar.

This only happens if I install the proprietary drivers for AMD (fglrx).

Additionally there is noticeable pixelation/garbled graphics throughout Gnome Shell after I install the drivers.

What is going on??

Install Gnome Tweak Tool and disable "Have file manager handle the desktop". Happened to me yesterday to, and i noticed that this option was enabled. When i disabled it the statusbar was fine again. 

Gnome Tweak Tool: 

```
sudo apt-get install gnome-tweak-tool
```

---

### Post by Vaphell on 2011-10-13
doesn't that prevent using desktop as a folder with files and stuff?

---

### Post by 8_Bit on 2011-10-14
Yeah it does. So it's just a temporary work-around, not really a fix. Thanks anyway though.

The global menu is gone now at least, but now I can't place icons on the desktop.

The garble is still all over the top menu and Activities too. Like Vaphell, the menu options are completely unreadable. Right now "Firefox Web Browser" reads as "**F r  fox W b Brow  r**" for example.

Seems like the garble is an upstream problem with AMD, hope they got on it and fix it!!

**EDIT**: Found another problem. Alt+F2 doesn't do anything in Ubuntu's version of Gnome Shell!
All these problems might just make me move back to Fedora until these issues are fixed D:, I never had problems with its interpretation of Gnome Shell.

---

### Post by crdlb on 2011-10-14
> **8_Bit said:**
> 
**EDIT**: Found another problem. Alt+F2 doesn't do anything in Ubuntu's version of Gnome Shell!
That key binding may have gotten unset. Check System Settings -> Keyboard -> Shortcuts -> System.

---

### Post by suprman2020 on 2011-10-14
> **Vaphell said:**
> doesn't that prevent using desktop as a folder with files and stuff?

Yes it does. Another option is to remove the appmenus.


EDIT: You can still have your desktop folder and files but it doesn't show up on your desktop.

---

### Post by NahsiN on 2011-10-16
I have the same problem as 8_bit. It seems the problem lies with the AMD catalyst drivers. It seems a lot more ppl are having the same problem. Solution is to install either catalyst 11.9 or revert to the oper source drivers. There is a good discussion on it here [http://ubuntuforums.org/showthread.php?t=1859626&page=3](http://ubuntuforums.org/showthread.php?t=1859626&page=3)

---

### Post by hannysabbagh on 2011-10-16
[B]hi guys.

you have to remove global-menu so you don't see it in gnome-shell:
sudo apt-get remove appmenu-gtk3 appmenu-gtk appmenu-qt
restart,and you can now have file manger on desktop without unity global-menu

and for alt+f2 command prompt follow these steps:
 open "System Settings" and under *Keyboard > Shortcuts > System*,  click "Disabled" next to "Show the run command prompt" and press ALT +  F2 , this should set ALT + F2 for running the command prompt.

thx and sorry for bad english :)
[/B]

---

### Post by Banyo on 2011-10-21
> **hannysabbagh said:**
> [B]hi guys.

you have to remove global-menu so you don't see it in gnome-shell:
sudo apt-get remove appmenu-gtk3 appmenu-gtk appmenu-qt
restart,and you can now have file manger on desktop without unity global-menu

and for alt+f2 command prompt follow these steps:
 open "System Settings" and under *Keyboard > Shortcuts > System*,  click "Disabled" next to "Show the run command prompt" and press ALT +  F2 , this should set ALT + F2 for running the command prompt.

thx and sorry for bad english :)
[/B]

Haha It worked! This guy saved the day!

---


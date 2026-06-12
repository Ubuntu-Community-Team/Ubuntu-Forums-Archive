---
title: "Slow computer, GNOME vs XFCE"
date: 2010-02-01
forum: General Help
---

### Post by Cityscape on 2010-02-01
Hi, I just installed Ubuntu CE on a PC with a 700 Mhz, 600 MB RAM, 64 MB graphics and a 30 GB HDD. It runs very slowly, but I've installed Ubuntu on a PC with almost identical spec before and it ran quite a bit faster. What could cause it to run so slow on this particular PC?

Im thinking about installing XFCE but I have a few questions:
1. Will it run faster with XFCE? How much faster do you think?
2. Will all my programs work with XFCE?
3. How easy is XFCE to use compared to GNOME?

4. And finally: How do I install XFCE?

All help is very much appreciated. :)

---

### Post by lykwydchykyn on 2010-02-01
Installing xfce is as simple as installing the xubuntu-desktop package.  Then just log out and choose "XFCE" from the "sessions" menu on the login screen.

I think you'll find on that hardware XFCE is still a bit slow. I'd recommend LXDE if you want to see a dramatic boost in performance.

Just install the lxde package and choose it from the sessions menu at login time.

---

### Post by Cityscape on 2010-02-01
Okay thanks. But so how easy to use is XFCE (compared to gnome), what about LXDE? Ease of use is a big issue for me as I'm new to Linux.

And my programs will work no matter which DE i use?

---

### Post by lykwydchykyn on 2010-02-01
> **Cityscape said:**
> Okay thanks. But so how easy to use is XFCE (compared to gnome), what about LXDE? Ease of use is a big issue for me as I'm new to Linux.

It depends on what you have to do.  They both provide most of what you expect from a desktop environment:  You have icons, panels, menus, etc. as well as some rudimentary utilities (config dialogs, text editor, picture viewer,etc).  If all you need from a desktop environment is the ability to click on icons and do basic file management, you're set.

What you tend to lose are non-core features.  For example, network browsing comes to mind.  In both XFCE and LXDE you (currently) have to mount a network drive to use it with the file manager, whereas in GNOME you can directly access network shares in the file manager.

If you don't use network shares, that's irrelevant.  

When it comes to system administration, the more "lightweight" your desktop is, the higher the probability that you'll need to hit the command line or edit a config file to change settings.  

Ultimately, you'll just have to try it and see.

> 
And my programs will work no matter which DE i use?

Most of the time, yes.  Sometimes, particularly with software that is part of GNOME or KDE, you might get graphical glitches, or it might require certain DE-specific services to be running.  But typically you won't have any problems.

---


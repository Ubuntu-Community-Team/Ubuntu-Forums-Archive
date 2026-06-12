---
title: "Is ther any Msconfig-like took in Ubuntu?"
date: 2006-04-05
forum: General Help
---

### Post by junglemike on 2006-04-05
HI all. Here's my problem. I have very old laptop w/ only 128mb of ram. KDE was too slow and memory-consuming for me. I downloaded XFCE desktop. It is much better now, but it still take kup almost all 128mb of ram upon startup (no apps started)
When i look in performance monitor, I see that most of the ram is occupied by models like these:
ksysguard
kded
klauncher
kdeinit
dcopserver
and many others.

Q1:
How can i disable autostartup of unneded modules?

Q2:
How do i know which modules are not needed?

Q3:any tips or links for increasing usability for old computers with slow cpu/ low mem (cpu:300mhz, ram=128mb)

Thanks in advance.

---

### Post by !nkubus on 2006-04-05
It's not in Kde but for gnome I think there is a program Called : BUM

[http://www.marzocca.net/linux/bum.html](http://www.marzocca.net/linux/bum.html)

i'm sure it will help

---

### Post by gingermark on 2006-04-05
[QUOTE=junglemike]Q3:any tips or links for increasing usability for old computers with slow cpu/ low mem (cpu:300mhz, ram=128mb)
[/QUOTE]

There are several Window Managers that use low resources you could try. I quite like Window Maker, but you might want to read [Window Managers for Beginners](http://ubuntuforums.org/showthread.php?t=87276) for details on the main ones and instructions on how to install them.

There is a third party metapackage that uses IceWM called [Ubuntu Lite](http://ubuntuforums.org/showthread.php?t=98233) specifically intended for your sort of specs. And Fluxbox always gets folks excited.

---

### Post by ncappel1 on 2006-04-07
You might want to have a look at this post too:

[http://ubuntuforums.org/showthread.php?t=89491&highlight=howto+ftp]("http://ubuntuforums.org/showthread.php?t=89491&highlight=howto+ftp")

this is very similar, but before you edit anything, write down what your defaults are, that way you can change them back if something goes a-wry (better safe than sorry!).

---

### Post by patrixl on 2006-04-08
I remember that XFCE has an option somewhere in its settings to load KDE services, or load GNOME services. I suspect that this is what's happening, since you have KDE services running. 

Or it could be that these KDE services are running because you use KDM as your login manager. But that wouldn't explain why ksysguard is in that list...

---

### Post by Velvet Elvis on 2006-04-08
Linux will use whatever memory you have available for caches and such.  It's normal for it to always use most all of your ram regardless of what you have running.

It's been a while since I've used XFCE, but I think there is a setting, maybe under profiles, that lets you disable the loading of gnome and KDE services upon XFCE startup.  That's what you are looking for.  The XFCE control isn't so expansive as it make it hard to find in more than a few minutes.  Uncheck the the two checkboxes and restart (log out and back in).

---

### Post by junglemike on 2006-04-08
Thanks for the help guys, I'm looking into it.
Great community.

---


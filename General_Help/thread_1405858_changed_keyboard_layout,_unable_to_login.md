---
title: "changed keyboard layout, unable to login"
date: 2010-02-13
forum: General Help
---

### Post by selahlynch on 2010-02-13
I changed my keyboard layout to arabic and now I can not login with my username and password.  Also I am unable to type my root password.  So I am completely locked out of my computer!!

I was a overwhelmed by the information I found from searching forums.  For now I'm working on making a bootable ubuntu CD so that I can run a live session and maybe fix this, but so far I am not having an easy time doing this.

Any other help would be appreciated.

Any advice about where to give feedback about this problem so it can be improved would also be appreciated.

---

### Post by zadehas on 2010-02-13
I think there's an option to change language at the login screen.

[IMG]http://news.softpedia.com/images/extra/LINUX/large/kde43ubuntu904-large_016.jpg[/IMG]

I think this will do the trick, but I'm not sure, I never had this problem.

---

### Post by selahlynch on 2010-02-14
Hey thanks for the suggestion.

"Select Language" changed the language of things on my screen but did not change my keyboard layout.  So when I type it still types arabic letters.

I've managed boot up my computer using an Ubuntu live CD and I can access all the files on my computer.  Now I need to figure out which configuration file to edit in order to change my keyboard layout.

Any suggestion as to which configuration file I need to edit to change my keyboard layout??

---

### Post by selahlynch on 2010-02-14
I found the file!

/etc/default/console-setup

I edited
XKBMODEL="pc105"
XKBLAYOUT="us"

And I was able to login... finally.  Hooray :)

---

### Post by homemadev on 2010-06-08
Hi. I have a similar problem. I need to change the layout at login from an English to a French keyboard. Following your input, I modified 

/etc/default/console-setup

FROM:

XKBMODEL="pc105"
XKBLAYOUT="us"
XKBVARIANT="dvorak"
XKBOPTIONS="lv3:ralt_switch"

TO:

XKBMODEL="pc105"
XKBLAYOUT="fr"
#XKBVARIANT="dvorak"
XKBOPTIONS="lv3:ralt_switch"

following some information I found at (([http://www.it.freebsd.org/pub/Unix/XFree86/WWW/htdocs/current/XKB-Config2.html](http://www.it.freebsd.org/pub/Unix/XFree86/WWW/htdocs/current/XKB-Config2.html)) ).. but when I rebooted the computer, the layout at the login prompt was still in US-Dvorak.

Have you experimented with /etc/X11/xorg.conf ? The same options are available.

EDIT: I'm (mostly) using Ubuntu 8.04 Hardy

---

### Post by homemadev on 2010-06-08
Ok..  /etc/X11/xorg.conf did the trick for me.

---


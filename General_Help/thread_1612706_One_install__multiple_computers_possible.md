---
title: "One install / multiple computers possible?"
date: 2010-11-03
forum: General Help
---

### Post by Floven de Sorezé Stockeir on 2010-11-03
Hello everyone,

this thread follows my previous one:
[http://ubuntuforums.org/showthread.php?t=1612674](http://ubuntuforums.org/showthread.php?t=1612674)

In there I explained how I wanted to have an install of Ubuntu on my external HDD that I could take with me and plug on any other computer to have it working thereon.

Apparently I overlooked the fact that hardware drivers are different from computer to computer.

My question thus is if anyone here happens to know of a way to make this happen, by means of generic drivers or such.

I know it is possible, yesterday I plugged my freshly installed external HDD on other computers where it ran ubuntu flawlessly. Now I started messing with it (installed driver updates etc...) and I can only access ubuntu on one laptop anymore.

Thank you very much for any help.

Floven de Sorezé Stockeir

---

### Post by alphaamanitin on 2010-11-03
Well, the only thing I can say, is look into what I mentioned before, a liveCD with permanance, or do what you did before and disable updates as that seemed to be what killed it.

AlphaA

---

### Post by oldfred on 2010-11-03
One user created a script:
Create Portable Ubuntu for 2 different Video Cards - script
[http://ubuntuforums.org/showthread.php?p=8107778](http://ubuntuforums.org/showthread.php?p=8107778)

Or use a generic driver that works for both your systems.

Boot parameter:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
Generic: xforcevesa or nouveau.modeset=0

or:
use the uvesafb to fix all the problems
[http://idyllictux.wordpress.com/](http://idyllictux.wordpress.com/)

---

### Post by Floven de Sorezé Stockeir on 2010-11-03
Thank you alphamaanitin, I take note of your suggestions.

I hope you don't mind I leave this thread open a little longer? Maybe I can collect other suggestions. I will put [Solved] first thing tomorrow morning though.

Again, thank you very much for your help. It's people like you who make linux what it is.

---

### Post by Floven de Sorezé Stockeir on 2010-11-03
Hey Oldfred, I'm about to go to bed now, but you've just excited me with your suggestions! I'll tell you how it goes, thank you very much!

---

### Post by Floven de Sorezé Stockeir on 2010-11-04
As Oldfred posted the link, 

[http://ubuntuforums.org/showthread.php?p=8107778](http://ubuntuforums.org/showthread.php?p=8107778)

Does anyone know how to activate this script (understandable for an inexperienced user)? Thank you very much.

> **P4man said:**
> for those interested:

```
#!/bin/bash
# copy appropriate xorg.conf for your videocard
cp /etc/X11/default.conf /etc/X11/xorg.conf
if lspci | grep "VGA compatible controller: nVidia" 
then
    # nVidia card
    nvidia-xconfig
fi
if lspci | grep "VGA compatible controller: ATI Technologies" 
then
    # ATI card, loading opensource ati driver
    cp /etc/X11/ati.conf /etc/X11/xorg.conf
fi
```Save it as /etc/rc2.d/S01nvidia-xconfig
Make it executable.
Then copy a default (mostly empty) xorg.conf as /etc/X11/default.conf
And modify one that loads ati driver (i use the opensource) and save it as /etc/X11/ati.conf
install nvidia drivers (on a machine with nvidia graphics), and off you go. 

I guess it may give problems if you try it on a machine with an old  nvidia card no longer supported by the 185 drivers, but other than that,  works fine.

---


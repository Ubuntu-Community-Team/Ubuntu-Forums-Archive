---
title: "How to create Ubuntu command line install with minimal graphical interface"
date: 2009-07-13
forum: General Help
---

### Post by pythonscript on 2009-07-13
I just installed command line only ubuntu desktop (booting 9.04 alternate install, then using the custom option) but I want a basic window manager/x server. For anyone that's used SystemRescueCD, I'm kind of trying to mimic that in my installation. I'm going to be making a live CD of this installation eventually, so my question is this. What packages should I install to have the basic x server, and how can I configure the system to not start said x server on boot? 
 
I'd like to configure it so that it only runs the command line, but if I run, say, gparted, which I prefer to the parted, it'll load the x server/window manager and boot the application. Any ideas? Thanks!

---

### Post by HotForLinux on 2009-07-13
I'm not an expert but I think that if you install a window manager, the package manager will install whatever else you need to use the x server. If not then install the package xserver-xorg-core but you'll probably need some other things like fonts.

You'll probably have to configure things later so that the X server and the graphical login don't start at boot time

If you want a light weight desktop you'll probably don't want to install neither gnome nor kde. 
xface, fluxbox and icewm are popular alternatives for that purpose.

> aptitude show icewm xfce4 fluxbox xserver-xorg-corewill show you some info and you can google for screenshots or more info about them.

and

> aptitude search icewm xfce fluxboxwill show you packages to expand the features of those  desktops

---

### Post by pythonscript on 2009-07-13
Which one of those would be the least hard drive intensive? I'm looking for something that takes up at as little space as possible.

EDIT:  Never mind; I forgot that apt tells me this when I install. Icewm looks like the winner here.

---

### Post by pythonscript on 2009-07-13
All right, I loaded icewm, but I guess I'm missing something... I run 

```
sudo startx
``` and icewm loads, but the only program I can start is Gparted. How do I start other applications? If possible, I'd like icewm to load a basic terminal as soon as it starts. Could I maybe script this? A script that starts with sudo startx, then runs a terminal? When I click on items in the icewm menus, they don't open! Unless it's gparted. That one opens for some reason.

---

### Post by HotForLinux on 2009-07-13
startx used to be the way to start the x-server but I believe that nowadays the right way to start gdm, as many other servers run by root is

sudo /etc/nit.d/gdm start

or

sudo invoke-rc.d gdm

So you can try and see if  /etc/nit.d/icewm or something similar exists in that directory

What do you mean by "the only program I can start is Gparted" that was the one you mentioned and that is EXACTLY the ONLY one you can run??

I have never used icewm. Maybe you should check with screenshots and see if what you have got is what is usual.

aptitude -s package_name

will do a dry run giving you the amount of space you need, not only for that particular package but for all the extra packages that need to be installed with it due to dependencies. But one thing is disk space and another is the load

Maybe you want also:
*icewm-gnome-support*

I read:
- "IceWM is small, fast and simple. Plus, it's practically ideal when used with the dfm file manager"
- "more is easy to configure using "icepref" which normally is in every dist but I suggest to search and install "IceMe" that flawless configure the menu bar."
 - "If you must
have icons on your desktop, then just start up kfm in your **.**Xclients file."


links:
[http://xwinman.org/icewm.php](http://xwinman.org/icewm.php)
[http://linux.softpedia.com/progScreenshots/IceWM-Screenshot-3302.html](http://linux.softpedia.com/progScreenshots/IceWM-Screenshot-3302.html) 
[http://www.icewm.org/manual/](http://www.icewm.org/manual/)
[http://www.icewm.org/FAQ/](http://www.icewm.org/FAQ/)


And now I see that there's a package called ***icewm-lite*** which seems to be even more light weighed than icewm. I read that it uses 2.5MB of RAM

---

### Post by pythonscript on 2009-09-05
It's working now, and I have a nice little diagnostics live cd set up. Thanks for the help!

---

### Post by Jose Catre-Vandis on 2009-09-05
Try slim or there are other real lightweight login managers. Alternatively, do without a login manager at all. You can set an auto startx after logging in at the command line. See [KMandlas speed up tutorial]("http://kmandla.wordpress.com/2008/05/04/howto-set-up-hardy-for-speed/") for more help. (It's for Hardy, but still valid)

---

### Post by ddrichardson on 2009-09-05
Does the xorg package not contain TWM any more?

---

### Post by pythonscript on 2009-09-06
I don't use a login manager right now. I don't see the use for a pretty looking login manager anyways; what's wrong with logging in at the terminal? Thanks for the guide, too; that's a ton of good information.

---


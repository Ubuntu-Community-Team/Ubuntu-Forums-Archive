---
title: "Can't log in to Ubuntu/gOS install"
date: 2010-11-10
forum: General Help
---

### Post by Pselus on 2010-11-10
My OS X kernel got fried recently and my dvd drive is screwed so I can't reinstall (yet).
I happened to have a 1.4gig partition that had an old copy of gOS installed so I booted into that to use the internet.  While there I updated the system to Ubuntu 10.04 via the Update Manager.  That ran fine, then I installed some programs and realized that I was running out of disk space (it got to the point where it wouldn't let me download a torrent file because there was no space).
I went to remove some programs via the Software Manager but when I clicked "Remove", nothing happened.  I waited about 5 minutes and still nothing happened.
Coming from a Windows world I figured a reboot would solve all my problems.  On reboot I am presented with the login screen and an error in the bottom right corner that says something about "Power Manager defaults" not set correctly.
The system lets me choose my user and put in my password...and then when I hit Log In, the screen flashes and for a split second I see text on a black background.  It's not long enough to read though.  And then I am back at the Log In screen with the same error and can repeat the whole process every time.
I have tried booting in "recovery mode" and halfway through that it just stops.

I am somewhat comfortable in the Terminal if I can figure out how to get there so is there some way to maybe clear off some of the bigger programs I have installed as I'm assuming the low disk space is the problem here?  The biggest issue is I don't even know how to get to the Terminal during boot.  What I have just typed up here is the extent of my Linux knowledge.

---

### Post by Hippytaff on 2010-11-10
In the terminal
```

sudo apt-get remove {packagename}

```
should uninstall packages.
Also ```
 sudo apt-get autoclean 
``` will clean up any un needed bits left behind from installing stuff.

---

### Post by Pselus on 2010-11-10
so that leads to some other questions:
1) How do I get to the terminal without being able to log in?
2) How do I find out what the package names are?
3) Will apt-get still work if apt-get wasn't what was used to install the package? (or is the Software Manager just a GUI on top of apt-get?

---

### Post by Hippytaff on 2010-11-10
Sorry
 
1) use a liveCD
2) Not sure, google or trial and error, do you know what your trying to uninstall
3) Apt-get should still work - also look into purge :-)

---

### Post by Pselus on 2010-11-10
I don't have a working DVD player on this machine (one of the reasons I'm even using gOS on the machine otherwise I'd just reinstall OS X)
The main package I was going to uninstall was NetBeans as I think it was the biggest I installed.

So there is no way to get to the command line or Terminal without a liveCD?
Thanks for your help though.

---

### Post by Hippytaff on 2010-11-10
LiveUSB
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---


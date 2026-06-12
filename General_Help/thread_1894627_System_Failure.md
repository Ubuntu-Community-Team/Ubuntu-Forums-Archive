---
title: "System Failure?"
date: 2011-12-13
forum: General Help
---

### Post by lonewolf69 on 2011-12-13
Hi All,

My ubuntu 11.10 froze so I rebooted, after it got past the grub boot loader my screen was normal but had a line on under the 4 dots..."Waiting for up to 60 seconds for network connections."  After about 2 minutes the screen goes blank and nothing!  What is going on?  I cant get to anything.

K

---

### Post by oldtimer7777 on 2011-12-13
Have you done any installations or updates during the last session? 

> **lonewolf69 said:**
> Hi All,

My ubuntu 11.10 froze so I rebooted, after it got past the grub boot loader my screen was normal but had a line on under the 4 dots..."Waiting for up to 60 seconds for network connections."  After about 2 minutes the screen goes blank and nothing!  What is going on?  I cant get to anything.

K

---

### Post by RealityMaster on 2011-12-13
Check out post #24

[https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/811441](https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/811441)

---

### Post by lonewolf69 on 2011-12-13
I did install 1 program through the software center.  I dont remember what it was (grrrr).

---

### Post by oldtimer7777 on 2011-12-13
> **lonewolf69 said:**
> I did install 1 program through the software center.  I dont remember what it was (grrrr).

That's probably it.  

"Get to the choppa, or they'll be nobody left to get to the choppa"

---

### Post by lonewolf69 on 2011-12-13
How do I uninstall it when I only get a black screen?

---

### Post by oldtimer7777 on 2011-12-13
> **lonewolf69 said:**
> How do I uninstall it when I only get a black screen?

Boot into recovery console?  Use an external live bootable usb of Ubuntu to boot your computer that does work?  Then you will have to find the changes made by the application you installed (whatever it was) and undo it manually.  It is a pain in the __.  The one thing Ubuntu lacks is a resque disc that you can boot from that will fix a broken system automatically like windows...  or is there something like that available on the alternative installation Ubuntu disc? The alternate disc has something like that feature, but I have only needed it once.  I'm sorry I don't remember.  You will have to research that.

---

### Post by lonewolf69 on 2011-12-13
Giving recovery console a shot.

---

### Post by lonewolf69 on 2011-12-13
I could only do a package check and get to a command prompt.  The package check fixed a couple things like clock.  I did a dir from the command and got a non-existent command or something like that.  

I remembered that I delete the downloaded file from desktop that was the 11.10 .tar.  Could this be it?  If so, how do I get it back when I cant use my system?

---

### Post by oldtimer7777 on 2011-12-13
> **lonewolf69 said:**
> I could only do a package check and get to a command prompt.  The package check fixed a couple things like clock.  I did a dir from the command and got a non-existent command or something like that.  

I remembered that I delete the downloaded file from desktop that was the 11.10 .tar.  Could this be it?  If so, how do I get it back when I cant use my system?

If you honestly can't remember what you did to manually undo whatever it is that was reconfigured, your best bet is to reinstall Ubuntu 11.10:

[https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)

And you migrate your data from your old broken Ubuntu partition over to your new home folder. If you reinstall from a USB Flash Drive instead of a disc, it only takes about 15-25 minutes to get everything back in business again, and less time it would probably take to figure out what broke on your old Ubuntu system.

---

### Post by lonewolf69 on 2011-12-13
Will I loose all my programs that I have installed?

---


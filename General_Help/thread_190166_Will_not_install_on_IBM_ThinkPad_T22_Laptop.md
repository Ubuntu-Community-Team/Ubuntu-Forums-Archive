---
title: "Will not install on IBM ThinkPad T22 Laptop"
date: 2006-06-05
forum: General Help
---

### Post by dylanknightrogers on 2006-06-05
Hi everyone,

Just wanted to let you know that Ubuntu Dapper will not install on my IBM ThinkPad T22 laptop.  It freezes before the CD-ROM starts the GNOME display manager.  It just quits.  I normally check the computer's status by hitting Capslock and seeing if it responds, but alas, nothing.  Please help!

The media is fine -- it works on my desktop, but not my laptop.  I'm stuck with Damn Small Linux until then, which, is actually quite fast.  But I miss Ubuntu.

Thanks for replies.

---

### Post by Poldi on 2006-06-13
I have Ubuntu 6.06 running on a T22. this is the 900 MHz version with 14.1" 1024*768 display and 384 MByte memory. I don't have the exact model number at hand just yet.

what might be interesting to you is that I did not install 6.06 fresh of the 'box' but apt-get dist-upgraded from Breezy. this might work for you as well even if the installer has problems.

---

### Post by stimpsonjcat on 2006-06-13
this is a known [bug]("https://launchpad.net/distros/ubuntu/+source/xserver-xorg-driver-savage/+bug/33617")and has to do with the new savage 3D driver in newer kernels.

you can use the alternate (text-mode) install disk, then boot your computer in "safe mode" and add/replace the lines in your /etc/X11/xorg.conf file as described in the bug report linked above.
hope that helps.

---

### Post by tedrogers on 2006-08-07
I have a similar problem on my T22 (with Savage gfx) using the Live DVD of Ubuntu v6.06. 

The only differnce is that my DVD ROM gets as far as the UBUNTU loader screen and on the second line of the loader, called mounting root filesystem, and my DVDROM just starts gurgling loudly and making all kinds of weird and nasty sounding noises!!  This continues in perpuity until I turn off the machine.

I found a boot option called floppy=thinkpad, but this made no difference.

The Live DVD is fine - it works on my dekstop no problems....as does the KUBUNTU Live DVD which works on my desktop but not the T22 laptop.

The DVDROM on my T22 presents no problems with any of these linux distros, inc Suse, Knoppix, Slax, DSL and Gentoo. Allof these work fine and I have no other problems with my DVD drive. 

I have not tried installing yet...because I want to try the Live version on the laptop first (hoping that it will see my broadcom chipset Wifi card?!?)

So what's the answer here anyone? Any help appreciated.

Thanks.

---

### Post by paulvbrown on 2006-08-18
Fairly certain that stimpsonjcat's reply has the answer there for you, but here's my reply to what I swear is the same problem:

[http://www.ubuntuforums.org/showthread.php?t=225588](http://www.ubuntuforums.org/showthread.php?t=225588)

-paul

---

### Post by wykedengel on 2006-09-18
was able to install 6.06 without problems following the method i posted in the hardware section of this forum:

[http://ubuntuforums.org/showthread.php?p=1514405#post1514405](http://ubuntuforums.org/showthread.php?p=1514405#post1514405)

---

### Post by tedrogers on 2006-09-19
> **wykedengel said:**
> was able to install 6.06 without problems following the method i posted in the hardware section of this forum:

[http://ubuntuforums.org/showthread.php?p=1514405#post1514405](http://ubuntuforums.org/showthread.php?p=1514405#post1514405)

Yes...you will find my lengthy exploration of the solution on there under TEDROGERS. Just follow that and it will be fine.

---


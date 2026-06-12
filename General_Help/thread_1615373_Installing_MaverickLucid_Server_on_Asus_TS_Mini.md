---
title: "Installing Maverick/Lucid Server on Asus TS Mini"
date: 2010-11-06
forum: General Help
---

### Post by aaronr8684 on 2010-11-06
Mentioned post - [http://wiki.ubuntuforums.org/showthread.php?t=1591198](http://wiki.ubuntuforums.org/showthread.php?t=1591198)

I was/am also having the same problem that was described above and fixed it with either 'nomodeset' or 'i915.modeset=0', however, once I installed Gnome (part of the "Ultimate Server Guide"), I had one of the following happen...

-On Maverick, it would continue to boot in the console and running commands like startx would result in an error (no screen)

-On Lucid, it stopped booting into the server all together (even with the above fixes). Once it boots into the server (about 6-7 seconds later), I'll see a bunch of reddish square artifacts on the screen and the HD activity will stop and the screen will remain on, but nothing will be displayed.

I've searched high and low for help on this and nothing seems to fix the problem. I consider myself very technical but my linux experience is only fair/good. Mostly from Unix experience in college and messing around with Ubuntu Desktop on my netbook. Thanks in advance for any help.

-Aaron

---

### Post by aaronr8684 on 2010-11-09
Another thought I've had, and I'd like confirmation before I try this. Would installing KDE or another alternate GUI be any different, or are they all based on X and, therefore, running the same way with a different look? Thanks again.

-Aaron

---

### Post by aaronr8684 on 2010-12-01
Does anyone have any ideas for this problem? If the answer is, "Ubuntu won't work in this situation", that's fine, but can someone point me in the right direction so that I'm not downloading random distros and trying them one at a time? Is it safe to assume that if the live disk of a distro works, that the full install will also work? Thanks.

-Aaron

---

### Post by roofnron on 2010-12-05
I too had the problem you had with same setup and found the answer at these sites:

[https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting)

and 

[https://edge.launchpad.net/~xorg-edgers/+archive/ppa](https://edge.launchpad.net/~xorg-edgers/+archive/ppa) (please read)

basically upgrading intel drivers with:

sudo add-apt-repository ppa:xorg-edgers/ppa

update and upgrade (takes a while) then reboot

You have to add the i915.modeset=0 again, then hopefully it will boot to the gui

After logging in, in terminal type

sudo gedit /etc/modprobe.d/i915-kms.conf  :then add

options i915 modeset=0

hit save and close, exit terminal. 

You shouldn't have to type the i915 thing at boot up anymore.

I hope this helps.

---

### Post by aaronr8684 on 2011-01-02
THANK YOU SO MUCH! After two months of trying everything I could find, this worked.

---

### Post by roofnron on 2011-01-03
Great, took me some digging to get it figured out myself.

---


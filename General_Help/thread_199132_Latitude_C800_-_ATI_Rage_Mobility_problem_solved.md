---
title: "Latitude C800 - ATI Rage Mobility problem solved"
date: 2006-06-18
forum: General Help
---

### Post by jrm4 on 2006-06-18
I saw a few things in the forums about people having problems with the display on a Dell Latitude C800 , ATI Rage Mobility M4.  I didn't see any specific solution, but I found one on my own (This is not for any XGL stuff, just to get the thing working without the weird "letterboxing")

The display problem I had was that, after login, the display would work, but parts of the screen would repeat and be unusable. I think this is due to this machine not being able to recognize "odd" resolutions; but for some reason, after my dapper install, it defaulted to one of those odd resolutions.

So, I ran the configuration thing with:

sudo dpkg-reconfigure xserver-org.

Changed driver from "ati" to the old school "vesa"

Tick only "regular" resolutions higher than 800x600.

Log back in and change the resolution from within gnome until you get one that works.

---

### Post by JeremyWorst on 2006-06-19
I've got an old Latitude 800C as well, with ATI Rage Mobility M4.  Works great as originally installed but only at 1280x1024 and 1400x1050.  Anything lower looks very distorted.  Problem is I'd like to play Doom on this laptop, and it seems to only run at low resolution.  I tried your suggestion to switch to vesa, but can't get past 
sudo dpkg-reconfigure xserver-org

I get an error message saying
jeremy@ubuntu:~$ sudo dpkg-reconfigure xserver-org
Package `xserver-org' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: xserver-org is not installed

Not even sure what this means.  Any ideas?

---

### Post by melotron on 2006-07-07
> **JeremyWorst said:**
> 

sudo dpkg-reconfigure xserver-org

I get an error message saying
jeremy@ubuntu:~$ sudo dpkg-reconfigure xserver-org
Package `xserver-org' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: xserver-org is not installed

Not even sure what this means.  Any ideas?

You must type sudo dpkg-reconfigure xserver-xorg (not xserver-org).:-D

---


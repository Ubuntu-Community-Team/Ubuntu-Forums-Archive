---
title: "Is VLC 1.x an option for Intrepid?"
date: 2010-07-28
forum: General Help
---

### Post by b_k_chu on 2010-07-28
hi,

i'm still on Intrepid (i know, i'm behind the times) and i've been poking around for simple-straightforward info on how to upgrade my VLC 0.9.4 to 1.x.....but everything i've found seems to assume one is already on Jaunty at least.  even videolan.org has simple-straightforward info for upgrading VLC for all distros as far back as Hardy....except for Intrepid.

and i'm half-tempted to just try following the steps given for those who are on Jaunty and just seeing what happens.....though i also can't help but think that it may be dangerous to do that.

so if videolan doesn't have info for Intrepid users, is it even an option?  or does it even matter at all which ubuntu version i'm on, and i'm worrying about it for nothing? xD

---

### Post by clhsharky on 2010-07-28
b_k_chu

Intrepid is a unsupported platform, why not upgrade to Jaunty?
They are very similar (grub,file system)mostly updated apps and kernel in Jaunty. Should be a fairly painless upgrade. Can be done off a alternate Jaunty CD.

Sharky

---

### Post by b_k_chu on 2010-07-29
> **clhsharky said:**
> b_k_chu

Intrepid is a unsupported platform, why not upgrade to Jaunty?
They are very similar (grub,file system)mostly updated apps and kernel in Jaunty. Should be a fairly painless upgrade. Can be done off a alternate Jaunty CD.

Sharky
not a very helpful answer, Sharky. >.>

---

-update-

adding these repos got me up to 1.0.0-rc2:
deb [http://ppa.launchpad.net/moviemaniac/ppa/ubuntu](http://ppa.launchpad.net/moviemaniac/ppa/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/moviemaniac/ppa/ubuntu](http://ppa.launchpad.net/moviemaniac/ppa/ubuntu) intrepid main

....which at least gets me the one feature i was looking for: the ability to advance a vid frame by frame. :3

edit: oops, forgot to note the key to be added for the above repos -- 
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 1501599E

---


---
title: "Xubuntu 12.04 cannot burn to CD-R"
date: 2012-05-03
forum: General Help
---

### Post by xtgyal on 2012-05-03
I just downloaded Xubuntu 12.04 from [http://mirror.anl.gov/pub/ubuntu-iso/CDs-Xubuntu/12.04/release/](http://mirror.anl.gov/pub/ubuntu-iso/CDs-Xubuntu/12.04/release/) and the ISO file is 713.3 MB, which doesn't allow me to burn to a 700 MB CD-R.  The instructions say it should be able to fit onto a CD, did I get the wrong file?  I'd hate to waste a DVD for just 14 MB.

---

### Post by cummins on 2012-05-03
Anybody have a fix for this?  I have the same problem.

ls -lh xubuntu-12.04-desktop-i386.iso  reports the file size is 681MB.  xfburn will write the CD, but it reports the image size is 713MB, and spits it out with an error message at the end.  I was able to boot from this potential coaster - haven't tried a full install yet, though - I am concerned that there is data missing and the install will fail at just the wrong moment.

---

### Post by RJARRRPCGP on 2012-05-03
What did it say at the end? 

I'm curious if it's complaining about being unable to scan the CD, because of it ejecting it before it could read the CD.

---

### Post by xtgyal on 2012-05-05
I tried burning the xubuntu-12.04-desktop-i386.iso (Xubuntu 12.04 32-bit) file using the default Brasero Disc Burner on Ubuntu 12.04.  Both Brasero and Nautilus show the ISO file size to be 713.3 MB.  Brasero ghosts the burn options and gives a "No Disc Available: Please replace the disc with a supported CD or DVD." error with a standard 700 MB CD-R, and unghosts with a standard DVD-R showing 4 GB of free space left over after burn.  It seems a shame to waste 4 GB of disc space though when its supposed to fit on a CD in the first place.  I'm trying to figure out if somehow I got the wrong file, or if not, then they need to update their info that it won't fit on a CD.  Might an alternative be to get the Xubuntu 11.10 ISO and then upgrade it after install?  I couldn't find a link on the Xubuntu site for older ISOs though.

---

### Post by jdi2728 on 2012-05-05
Hi,

Downloaded the amd-64 xubuntu. Properties show 729.1mb burnt with no problem with k3b and nero linux onto normal cd-r. Just install on laptop with no problems. My suggestion is to try k3b.:)

---

### Post by cummins on 2012-05-09
Looks like RJARRRPCGP might be right about this.  I just tried it again, so I could note the error message and report back here - but this time I unchecked the 'Eject disk' option, and it completed without any errors.

I'm still using xfburn.  I looked at installing k3b, but it wants to pull in over 200MB of dependencies.

Thanks all for your help!  I think I actually have 2 good CDs now.

So, really, this question remains: why is the iso image size 713.3MB, intended for a 700MB cd?  It just looks like impending doom to see that on the screen when you're about to press the Burn image button.

---


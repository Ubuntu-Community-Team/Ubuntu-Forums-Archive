---
title: "USB  and blank CD - no automount in 9.10"
date: 2009-10-30
forum: General Help
---

### Post by jrrader on 2009-10-30
I just did a clean install of 9.10 and now I'm trying to burn the 32 bit version for my wifes computer (I did an upgrade on hers and there are some problems so I'm going to do a clean install on hers too).  Problem is, when I put a CD in my drive it doesn't mount it.  Same thing when I put a USB flash drive in - nothing.  I burn a lot of CDs and DVDs for my work.  It's not a hardware problem because they still work in Fedora, Crunchbang, and Win7 - but I don't use those for work.  I'd really appreciate some help.

---

### Post by jrrader on 2009-10-30
Okay, I seemed to have solved this myself.  I only did two things so I'm guessing this fixed it.  Google search told me to run some command in gnome-mount.  I found gnome-mount wasn't installed so I installed it.  Read the man page for gnome-mount and it said that I should never have to read the man page for gnome-mount... because gnome-volume-manager takes care of all that stuff for the end user.  gnome-volume-manager was not installed so I installed that as well.  Restarted and everything mounted properly.

---

### Post by davmac on 2009-11-01
Fantastic! Thanks for updating this one with the solution. You;ve just saved me a load of time trying to figure this out. Top work!

---

### Post by peculiar penguin on 2009-11-01
Weird, my clean Karmic install automounts my flash drives and CDs just fine, and neither gnome-mount nor gnome-volume-manager are installed.

---

### Post by jrrader on 2009-11-01
Update - After doing this I had an icon on my desktop for "Blank CD-R" at all times. After searching for an answer for a few hours and finding none, I decided it would take less time to reinstall (formatted everything but /home and ran my "freshstart.sh" to download all the applications I need on a new install).  Now everything works fine - without the packages mentioned above.  I really don't know what is going on.

Also, with the first install one of my NTFS storage partitions was not being seen by ubuntu.  I have two that I mount through fstab but it was only seeing one of them.  After the reinstall the second one came back.

---

### Post by BrandonBan6 on 2009-11-02
I'm having this same issue!The gnome-conf automount keys are enabled, FSTAB looks normal.. I'll give gnome-mount a shot and update.

---

### Post by mad_ady on 2009-11-16
Hello,

I had the same problem too - after an upgrade from the previous version (Xubuntu). After installing gnome-volume-manager everything works (Thanks!). The problem seems to be from a conflict between brasero (which was installed in the older version) and nautilus-cd-burner (or something similar). gnome-volume-manager asks for nautilus-cd-burner to be installed, but this is installed only if brasero is removed. My guess the update process doesn't automatically remove brasero if it's found so it can't install gnome-volume-manager.

By the way, after installing gnome-volume-manager, I removed nautilus-cd-burner and reinstalled brasero and things still work...

---

### Post by htor on 2010-03-30
Thank you, jrrader.

---

### Post by celem on 2010-03-30
Thanks jrrader and mad_ady - I was having the same problem in 9.10 and after following your advice all is well!

---

### Post by Bernard Hurley on 2010-05-12
In lucid a better solution might be might be to just remove the package "usbmount" as suggested in:
[http://ubuntuforums.org/showthread.php?t=1468755](http://ubuntuforums.org/showthread.php?t=1468755)

Since lucid doesn't have the package gnome-volume-manager, if it is in your startup apps, you might as well remove it so that gnome doesn't waste time looking for it!

---


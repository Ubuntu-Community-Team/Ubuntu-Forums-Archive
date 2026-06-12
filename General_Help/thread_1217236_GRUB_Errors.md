---
title: "GRUB Errors"
date: 2009-07-19
forum: General Help
---

### Post by jfreak53 on 2009-07-19
Ok for the past two days I am having some trouble booting with grub.  It only happens after I shutdown ubuntu and turn off pc.  When I go to boot back up it gives me this error when it get's to the "Grub loading" part, error 18, and it won't load the menu.  Both times I have had to use super auto grub boot cd and reload grub onto the MBR of the first drive.  Then it works until I shutdown ubuntu again, and the error comes back.

What's going on here?  Thanks for any help.  I found a couple of posts already on this subject but this is not the case with mine.  I have two disks.  Primary running windows, one windows install for work and another on a logical (ext) partition running a games install of xp.  So two XP install in two separate partitions on primary drive.  Then secondary drive has linux installed on two parts.  One / and one swap.  GRUB is loading from primary IDE.  Is there any other way to fix this other than deleting all partitions and starting over.  I have had this installed this way for over 3 weeks now and this just starting happening.

---

### Post by utnubuuser on 2009-07-19
What have you tried?

Tried reinstalling grub through a live cd?
[http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")

---

### Post by lindsay7 on 2009-07-19
I had a similar problem a few months ago.  Here was the fix for me.

[http://ubuntuforums.org/showthread.php?p=6891867#post6891867](http://ubuntuforums.org/showthread.php?p=6891867#post6891867)

---

### Post by jfreak53 on 2009-07-21
Yes I have tried re-installing grub, like I said up there I use super auto grub disk, which is a grub restoration util.  It boots then using your root linux dir and your menu.lst it will re-install grub from scratch.  That's the main problem I do that and it keeps coming back.  Linux works fine, that's not a problem.  I'm half tempted just to install another boot loader.  This is crazy.

---


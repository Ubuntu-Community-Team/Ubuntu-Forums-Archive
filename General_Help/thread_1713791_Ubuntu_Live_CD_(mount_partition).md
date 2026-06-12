---
title: "Ubuntu Live CD (mount partition?)"
date: 2011-03-24
forum: General Help
---

### Post by Mercenary(FH) on 2011-03-24
Quick question, the 32 bit live cd for ubuntu, can you mount say a windows partition within it and drag off the files from windows onto a flash drive? or does the Ubuntu live CD not allow you to do this?

its on a laptop btw

---

### Post by ajgreeny on 2011-03-24
> **Mercenary(FH) said:**
> Quick question, the 32 bit live cd for ubuntu, can you mount say a windows partition within it and drag off the files from windows onto a flash drive? or does the Ubuntu live CD not allow you to do this?

its on a laptop btw
This is one of the very useful properties of a live ubuntu CD, or almost any other linux distro.  They can be used to rescue broken windows installs and get the personal files that you can no longer get to if your windows install is broken.

Just boot to the live desktop, double click on the windows partition which will show in Places,and you should see all your files in nautilus.  If you want to copy them to a usb thumb drive, or external drive you may need to do it with nautilus as root which you can do with the command "gksu nautilus" but try first without root permissions; it is a long time since I have had a windows partition to use, so I can't remember if root is needed for files on a ntfs partition..

---

### Post by Mercenary(FH) on 2011-03-24
Ok Ill check. Thanks man!

 edit: couldn't I just mount the partition with the little "mount" tray icon, then drag them to the external.?

---

### Post by ajgreeny on 2011-03-25
> **Mercenary(FH) said:**
> Ok Ill check. Thanks man!

 edit: couldn't I just mount the partition with the little "mount" tray icon, then drag them to the external.?
I've no idea.  Try it and see!

---


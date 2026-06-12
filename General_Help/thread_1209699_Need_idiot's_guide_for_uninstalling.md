---
title: "Need idiot's guide for uninstalling"
date: 2009-07-10
forum: General Help
---

### Post by TheMuse on 2009-07-10
I'm in need of an idiot's guide for uninstalling Kubuntu 8.1 w/KDE 4.2 on a dual boot laptop with Vista Home Premium and no disks.  Toshiba, in their infinite wisdom, decided not to provide the disks with a new laptop.  I installed Intrepid but alas, I'm too impatient to figure it all out so it's making me feel too stupid to live.  Someday I'd like to be able to use linux fulltime but for now I just don't have the time to learn it.

---

### Post by jerome1232 on 2009-07-10
First Download this vista recovery console cd
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

use it to drop to a command prompt and run this

(i'm not sure if you need the bootrec.exe portion)
```
bootrec.exe /fixmbr
bootrec.exe /fixboot
```

Then reboot, boot into windows, format kubuntu's partitions using vista disk managment tool (Start - Control Panel - Administrative Tools - Computer Management - Storage - Disk Management) then expand your ntfs partition out to the full disk.

If you can't expand ntfs disks on the fly (I think you can), then I'd suggest using a gparted bootable cd to expand your partition back out to the full disk.
Gparted live cd can be found here [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by TheMuse on 2009-07-10
Thank you so much for the quick reply!  I'll give that a shot tonight after work.  I'll let you know how it goes.

---

### Post by TheMuse on 2009-07-11
I finally figured out what I was doing wrong in Kubuntu but I did download and burn the recovery disk for Vista (YUCK!)  The only thing I'm having a problem with now is getting the ethernet to connect to the internet/network.  I tried setting it up manually, which I have to do, but it won't connect.  There's two ethernet cards on this laptop.  One for LAN and the other for WiFi and I have no idea which is the (only) one that's showing up in the dialog box for connections.

---


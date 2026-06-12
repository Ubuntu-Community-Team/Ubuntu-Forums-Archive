---
title: "my cd rom drive and storage partition will not mount"
date: 2009-07-13
forum: General Help
---

### Post by jcm1107 on 2009-07-13
Hi, all my media will not mount, it says that I don't have permission to mount when I try to open it. My usb hard drive is the only thing that still works. Could someone please help with this? I need to be able to play cd's and access my other partitions. I used to be able to so I don't know what has changed. Thanks!

---

### Post by jcm1107 on 2009-07-14
bump

---

### Post by jcm1107 on 2009-07-15
FIXED MY PROBLEM!!! I don't know what caused it but I had to run chkdsk /f in a command prompt to schedule chkdsk on next reboot I had to chkdsk like this twice and rebooted several times to make it take effect! How I found I needed to do this was I saw on Gparted partition editor that there was a warning. I ran Gparted live cd and looked at the information for that partition and it told me to run chkdsk /f and that is what got all my devices to mount again!! I dont know why this would of made the cd rom not mount but it is all fixed!! Also it made a storage partition not mount and that is now fixed just by fixing the windows partition!! I would like to know why the windows partition affected anything in Ubuntu?

---


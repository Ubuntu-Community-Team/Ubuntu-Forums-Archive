---
title: "Error trying to unmount SD cards"
date: 2012-08-05
forum: General Help
---

### Post by marianoa on 2012-08-05
Hi, I'm having problems trying to unmount an SD card. If I try the command

```
sudo umount /media/SDcard-id
```apparently nothing happens and in dmesg I get

```
[  116.329405] umount[2279]: segfault at 805759a ip 0805759a sp bfad3f38 error 15 in umount[8057000+1000]
```for each attempt. I tried with 2 different SD cards and I have the same problem.

Thanks

---

### Post by marianoa on 2012-10-11
Some updates about the problem, the problem regards umount and not the specific file system that I try to unmount. After booting the command 

```
umount
```outputs a plain a segmentation fault message. If I reinstall the package "mount" the command works ok and I'm able to unmount the filesystems. The problem is that now after every reboot the command umount gives a segmentation fault and I'm forced to reinstall the "mount" package again to make it work.
It looks like the executable file "/bin/umount" gets modified and broken after rebooting in fact I get the following output from "stat" before and after rebooting
```
  
File: "/bin/umount"
  Dim.: 67720         Blocchi: 136        Blocco di IO: 4096   file regolare
Device: 805h/2053d    Inode: 5636861     Coll.: 1
Accesso: (4755/-rwsr-xr-x)  Uid: (    0/    root)   Gid: (    0/    root)
Accesso  : 2012-10-11 18:41:32.000000000 +0200
Modifica : 2012-03-30 06:49:34.000000000 +0200
Cambio   : 2012-10-11 18:41:33.257412584 +0200
Creazione: -

``` 

```

  File: "/bin/umount"
  Dim.: 71816         Blocchi: 144        Blocco di IO: 4096   file regolare
Device: 805h/2053d    Inode: 5636861     Coll.: 1
Accesso: (4755/-rwsr-xr-x)  Uid: (    0/    root)   Gid: (    0/    root)
Accesso  : 2012-10-11 18:41:32.000000000 +0200
Modifica : 2012-10-11 19:09:46.013811455 +0200
Cambio   : 2012-10-11 19:09:46.013811455 +0200
Creazione: -

```

Any idea?

---

### Post by marianoa on 2012-10-14
Hi, I've got further details on the issue, looks like umount gets broken even if no reboot takes place, I can't figure out what triggers the problem. Any suggestion? Bump?

---

### Post by tea for one on 2012-10-14
Good morning

In nautilus, when you select the SD card drive with a "right click",
do you have options of:-

(a) eject
(b) safely remove drive

If you "eject" the SD card, the card is unmounted and the drive will hopefully remain active.

If you "safely remove drive", the drive is disabled (inactive) until you reboot.

I do not not why this occurs but I suspect that it is related to hardware.

SD cards often need to be treated like removable CDs.

Admittedly, the syntax is baffling.........

I would be interested to know what happens if you select "eject"

---

### Post by marianoa on 2012-10-14
Hi Tea for One,

thanks for coming to the rescue. I've just just tried both "eject" and "safely remove drive" and the message I get in nautilus is "One or more partitions are busy on /dev/sdb". Then I checked the command umount and it was broken (it gives a segfault if I execute it in the terminal with no arguments, it should print a few help lines instead). I reinstalled the "mount" package and then umount is working as expected in the terminal and I can both eject and safely remove the drive. Looks like the error messages I get in nautilus are just a consequence of umount getting broken somehow.

Thanks again for trying to help!

---


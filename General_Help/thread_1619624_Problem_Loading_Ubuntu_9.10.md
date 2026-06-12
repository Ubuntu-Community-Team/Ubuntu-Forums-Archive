---
title: "Problem Loading Ubuntu 9.10"
date: 2010-11-12
forum: General Help
---

### Post by lost-fan on 2010-11-12
Hi all,

I am using Ubuntu 9.10, dual-boot with Windows Vista. I am facing several problems with my Ubuntu and the following problems occur randomly, i.e. sometimes it occurs, sometimes it doesn't.

1) After a recent update on my update manager, I could not load my Ubuntu. Usually, we should see 3 things when starting ubuntu, (a) an Ubuntu logo (b) the word Ubuntu with status of the loading process beneath it (c) the main login window. My problem is after Step (a), the loading halts with a blinking cursor. It could not proceeed. I need to turn off my laptop and start it again. No problem after that. Any solutions?

2) Sometimes the loading halts after showing fsck...... 

3) Sometimes it halts after showing a list of loaded modems, i.e.

Loading Zte modem....
Loading ??? modem...
Loading ??? modem...

As I said, all the 3 problems above occured quite random. Any help?

Thank you

---

### Post by Rubi1200 on 2010-11-12
Hi and welcome to the forums :)

Please post the following information:

1. computer specifications, especially RAM and graphics card

2. how you connect to the Internet

3. the output of the following commands (if you can get into Ubuntu)

```
sudo fdisk -l
```

```
sudo dpkg --configure -a
```
These are run from the terminal which you can find under Applications > Accessories

Thanks.

---

### Post by lost-fan on 2010-11-12
Hi,

1) I am using 2 GB DDR3. My graphics card is nVidia Corporation G98 [GeForce 9300M GS]
For the graphics card, I am using driver 195.36.15 

2) I am using wifi. My modem is TP-LINK

3) root@wilson-laptop:/home/wilson# **sudo fdisk -l**

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc3ffc3ff

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11601    93184000    7  HPFS/NTFS
/dev/sda2           11601       13004    11264000    7  HPFS/NTFS
/dev/sda3           13005       28476   124272123+   f  W95 Ext'd (LBA)
/dev/sda4           28476       30402    15471448   12  Compaq diagnostics
/dev/sda5           24509       28476    31863808    7  HPFS/NTFS
/dev/sda6           13005       15436    19535008+  83  Linux
/dev/sda7           24036       24508     3799341   82  Linux swap / Solaris

Partition table entries are not in disk order

There is no output when doing sudo dpkg --configure -a

Thanks for ur help!

---

### Post by Rubi1200 on 2010-11-12
Seems fairly normal. Have you had this problem before or only after this recent update?

You could try running this command also and see if there is any change/errors:

```
sudo apt-get install -f
```

Let us know please.

---


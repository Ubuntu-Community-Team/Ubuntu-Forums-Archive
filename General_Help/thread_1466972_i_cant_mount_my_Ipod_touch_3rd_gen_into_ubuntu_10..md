---
title: "i cant mount my Ipod touch 3rd gen into ubuntu 10.04"
date: 2010-04-30
forum: General Help
---

### Post by uiuiui172 on 2010-04-30
i have checked everywhere in my filesystem! i also noticed in the /mnt directory there are no files. if that is the problem, the can someone please post the default mount directories. i also installed all additional libraries.

---

### Post by uiuiui172 on 2010-04-30
i need help!

---

### Post by kslen on 2010-04-30
All automatic mounts go in "/media" in Ubuntu.

If the device didn't get a proper name similar to the irl name of the device, then it might accessible through an obscure name.   

Open "Places -> Computer" and see if a device pops up in that window when you insert your iPod into a USB port.    

Or you can type "mount" and see if you recognize the partition size.

---

### Post by uiuiui172 on 2010-04-30
i checked in all the usb but they are all blank but my ipod says it is connected and charging

---

### Post by uiuiui172 on 2010-04-30
i also checked under computer! ive searced everywhere! I had no problem with this on the alpha version

---

### Post by kslen on 2010-04-30
Show me the last 10 lines of "dmesg | grep sd" just after you have removed and inserted the iPod into the USB port.

Also, show me the output of "sudo fdisk -l".

---

### Post by uiuiui172 on 2010-04-30
[    0.947732] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.947776] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.948042]  sda:
[    0.958802]  sda1 sda2 <
[    1.005152]  sda5 >
[    1.006079] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.788139] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    9.187905] Adding 3005432k swap on /dev/sda5.  Priority:-1 extents:1 across:3005432k 
 
and

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00046383

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9356    75143168   83  Linux
/dev/sda2            9356        9730     3005441    5  Extended
/dev/sda5            9356        9730     3005440   82  Linux swap / Solaris

---

### Post by kslen on 2010-04-30
Hmf, well. Then there's no easy solution afaik. :S

However, I did search a bit for "ipod touch ubuntu" and read about iFuse aka. "libipod". Got this installed? It aparently adds a layer to FUSE which allows for communication with the iPods.

[http://www.ubuntugeek.com/how-to-connect-iphoneipod-touch-using-usbin-karmicjauntyintrepidhardy.html](http://www.ubuntugeek.com/how-to-connect-iphoneipod-touch-using-usbin-karmicjauntyintrepidhardy.html)

Maybe this might be a step in the right direction as it seems that your current Ubuntu installation seems to lack software which recognizes the iPod when it's inserted to your system.

---

### Post by uiuiui172 on 2010-04-30
i do have it installed

---

### Post by uiuiui172 on 2010-04-30
i had fuse installed but not libipod-cl so i installed it. do i reboot?

---

### Post by kslen on 2010-04-30
If it doesn't work without rebooting, it wouldn't hurt to try. :p

---

### Post by uiuiui172 on 2010-04-30
ok brb

---

### Post by uiuiui172 on 2010-04-30
i got it! thank you sooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooo much!

---

### Post by pcrat on 2010-04-30
I have a 32GIG 3rd Gen Ipod Touch, Jailbroken, ( tethered of course ) when i plug in , usb, the usb icon shows up.. i can browse folders,, but i cant use any programs to transfer music, videos, but i can transfer pictures through the usb icon,, but they just dont have a thumbnail...  i have windows xp in a Virtual machine for the ipod.. and other stuff also..  i know. i wish there was an easier way for ubuntu 10.04 to reconize & transfer files.  I wish ya alot of luck buddy...

---

### Post by Morrog on 2010-05-01
i also cannot have my ubuntu 10.04 recognize my ipod touch 3G. however when i installed  libipod everything seems to be working smoothly. strange that it doesn't work out of the box as advertised though.

---


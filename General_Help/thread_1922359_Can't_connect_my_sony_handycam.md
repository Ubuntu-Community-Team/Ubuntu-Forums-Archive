---
title: "Can't connect my sony handycam"
date: 2012-02-08
forum: General Help
---

### Post by bluenose1982 on 2012-02-08
Hi All,

I've brought a Sony handycam cx115 and I can't see it in ubuntu 11.04

I've connected it via usb and expected it to just pop up on the desktop as a mass storage device but this hasn't happened.  I am still beginner level so don't really know where to start but I have done a dmesg and got this;

[   84.414925] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[   84.414953]  sdb: sdb1
[   84.427047] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[   84.427064] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[  134.111227] usb 1-7: USB disconnect, address 2
[  417.405102] composite sync not supported
[ 3666.109102] usb 1-3: new high speed USB device using ehci_hcd and address 3
[ 3666.242219] scsi7 : usb-storage 1-3:1.0
[ 3667.241276] scsi 7:0:0:0: Direct-Access     Sony     Camcorder        1.00 PQ: 0 ANSI: 0
[ 3667.242903] sd 7:0:0:0: Attached scsi generic sg2 type 0
[ 3667.243901] sd 7:0:0:0: [sdb] 124925952 512-byte logical blocks: (63.9 GB/59.5 GiB)
[ 3667.245899] sd 7:0:0:0: [sdb] Write Protect is on
[ 3667.245915] sd 7:0:0:0: [sdb] Mode Sense: 03 00 80 00
[ 3667.245922] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[ 3667.255067] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[ 3667.255099]  sdb: sdb1
[ 3667.262806] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[ 3667.262821] sd 7:0:0:0: [sdb] Attached SCSI removable disk
[ 4526.381058] usb 1-3: USB disconnect, address 3
[ 5233.264100] usb 1-3: new high speed USB device using ehci_hcd and address 4
[ 5233.398304] scsi8 : usb-storage 1-3:1.0
[ 5234.397296] scsi 8:0:0:0: Direct-Access     Sony     Camcorder        1.00 PQ: 0 ANSI: 0
[ 5234.399287] sd 8:0:0:0: Attached scsi generic sg2 type 0
[ 5234.413615] sd 8:0:0:0: [sdb] 124925952 512-byte logical blocks: (63.9 GB/59.5 GiB)
[ 5234.414501] sd 8:0:0:0: [sdb] Write Protect is on
[ 5234.414513] sd 8:0:0:0: [sdb] Mode Sense: 03 00 80 00
[ 5234.414522] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[ 5234.422372] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[ 5234.422403]  sdb: sdb1
[ 5234.429858] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[ 5234.429873] sd 8:0:0:0: [sdb] Attached SCSI removable disk


so i know it can see a Sony camera but have no idea how to get in to .  Please help!

Thanks

---

### Post by Rodney9 on 2012-02-08
[http://ubuntuforums.org/showthread.php?t=1476244&page=2](http://ubuntuforums.org/showthread.php?t=1476244&page=2)

It may use a "sony memory stick" there are seemingly drm and other Sony created problems with reading these if do a search.

Your camera maybe able to use a ordinary SD card that Ubuntu could read.

Rodney

---

### Post by bluenose1982 on 2012-02-08
hi, thanks for the reply, it is using a transcend sdxc card

---

### Post by bluenose1982 on 2012-02-09
any more suggestions? still can't get it working

---

### Post by winh8r on 2012-02-09
Not saying this will work for sure but it might, I used it to get access to a panasonic Lumix camera that wasn't showing up:

Plug the camera into a different USB port, if you are using a front port use one on the rear of the machine.

Switch on the camera

Leave it switched on and reboot your computer.

The camera should show up as a mass storage device when system reboots.

If it doesn't work then you have lost nothing but a couple of minutes, and you got an apology from me beforehand!!!

---

### Post by bluenose1982 on 2012-02-10
Thanks for the ideas but still no luck.  I tried the raw1394 commands

    /sbin/modprobe raw1394 
    /sbin/modprobe dv1394 

and

mknod /dev/raw1394 c 171 0 
mknod /dev/video1394 c 172 0 

as suggested but still don't work.

I think i'm going to get a card reader and see if that helps..

---


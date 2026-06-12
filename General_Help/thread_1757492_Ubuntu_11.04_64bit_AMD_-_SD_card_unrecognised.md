---
title: "Ubuntu 11.04 64bit AMD - SD card unrecognised"
date: 2011-05-13
forum: General Help
---

### Post by rekkie on 2011-05-13
Ever since upgrading from Ubuntu 10.10 to 11.04 I am unable to mount SD cards on my system. Previously all I had to do was plug them in and they were recognised and mounted.

when I run dmesg and fdisk, here is what I get. Does anyone have any idea what the problem might be?

root@mydesk-desktop:~# dmesg | tail 

[ 9046.150074] usb 4-4: new full speed USB device using ohci_hcd and address 2
[ 9046.516786] usbcore: registered new interface driver uas
[ 9046.548854] Initializing USB Mass Storage driver...
[ 9046.549157] usb-storage 4-4:1.0: Quirks match for vid 045e pid ffff: 400
[ 9046.549240] scsi6 : usb-storage 4-4:1.0
[ 9046.549667] usbcore: registered new interface driver usb-storage
[ 9046.549675] USB Mass Storage support registered.
[ 9047.547110] scsi scan: INQUIRY result too short (5), using 36
[ 9047.547127] scsi 6:0:0:0: Direct-Access                                    PQ: 0 ANSI: 0
[ 9047.548620] sd 6:0:0:0: Attached scsi generic sg2 type 0
[ 9047.557092] sd 6:0:0:0: [sdb] 7743488 512-byte logical blocks: (3.96 GB/3.69 GiB)
[ 9047.563273] sd 6:0:0:0: [sdb] Write Protect is off
[ 9047.563283] sd 6:0:0:0: [sdb] Mode Sense: 00 06 00 00
[ 9078.240115] usb 4-4: reset full speed USB device using ohci_hcd and address 2




root@mydesk-desktop:~# fdisk -l

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x32307566

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13        6375    51096576    7  HPFS/NTFS
/dev/sda3            6375        6435      488448   82  Linux swap / Solaris
/dev/sda4            9476      182402  1389030208    5  Extended
/dev/sda5            9476       34971   204796588+  83  Linux
/dev/sda6           34972       90124   443016441    7  HPFS/NTFS
/dev/sda7           90125      181651   735187968   83  Linux
/dev/sda8          181651      182402     6027264   82  Linux swap / Solaris


in dmesg, the card seems to be recognised correctly as a 4GB card, however fdisk does not see anything. Are there any other commands I can run to diagnose the problem?

thanks

Rekkie

---

### Post by Lazaruss on 2011-05-13
The reader appears to be on USB, does <lsusb> give anything?

---

### Post by rekkie on 2011-05-14
Thanks for the reply, here is what I get from dmesg and lsusb. Are there any other test I can try?

[  839.650089] usb 4-4: new full speed USB device using ohci_hcd and address 2
[  840.003328] usbcore: registered new interface driver uas
[  840.023136] Initializing USB Mass Storage driver...
[  840.023414] usb-storage 4-4:1.0: Quirks match for vid 045e pid ffff: 400
[  840.023563] scsi6 : usb-storage 4-4:1.0
[  840.023679] usbcore: registered new interface driver usb-storage
[  840.023680] USB Mass Storage support registered.
[  841.027194] scsi scan: INQUIRY result too short (5), using 36
[  841.027209] scsi 6:0:0:0: Direct-Access                                    PQ: 0 ANSI: 0
[  841.028722] sd 6:0:0:0: Attached scsi generic sg2 type 0
[  841.037196] sd 6:0:0:0: [sdb] 7743488 512-byte logical blocks: (3.96 GB/3.69 GiB)
[  841.043190] sd 6:0:0:0: [sdb] Write Protect is off
[  841.043200] sd 6:0:0:0: [sdb] Mode Sense: 00 06 00 00


from lsusb I get...

Bus 008 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 045e:ffff Microsoft Corp. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by sectshun8 on 2011-05-14
I've noticed the same on my Acer AOA-150... it has two SD slots... one generally acts as a reader, the other for expandable storage.  Since going from XP to 11.04, neither one recognizes a SD card when they are inserted.

I haen't tried yet, but I thought I read somehwere that it will recognize them if you boot the machine with the cards inserted... but still, that's crap.

I have yet to do any of the internet updates after the install, so I wasn't sure if perhaps that was an issue with it.

---

### Post by sectshun8 on 2011-05-14
I did actaully check the whole booting with teh SD card already inserted, and it will read it.  A 4Gb SD comes up as a 4.1GB Filesystem with a littel SD card graphic on the desktop.

It also contines to work if I remove the card and plug it back in...

---

### Post by ZaHACKieL on 2011-05-17
I'm having the same problem on a Dell XPS 17. It has a 9 in 1 media card reader, I tried with a SD and a mini SD (with adapter) and didn't work either. I'm also in Ubuntu 11.04 64bit

---

### Post by rekkie on 2011-05-23
I am still unable to see the card using Ubuntu 11.04 64 bit, however if I boot off an Ubuntu 10.4.1 x32 live CD, the card is seen correctly and everything works.

---

### Post by ZaHACKieL on 2011-05-30
Do you know if there's already a report on launchpad about this issue?

---

### Post by thenudehamster on 2011-05-30
I hadn't tried mine until I read this, but on mine it works perfectly - except that it shows the SD card as a USB thumb-drive. However, I'm using an hp G62 laptop with dual core AMD 64, but 32-bit Natty. I played safe and did a 32-bit install because I'd heard of a few issues with the 64-bit version; maybe this is one of them?

---

### Post by ZaHACKieL on 2011-06-02
@thenudehamster : I have a Dell XPS 17 laptop and a Toshiba NB505 netbook. Both have Natty 64bit but it's in the XPS where the SD doesn't work. The netbook works with exactly the same Natty installation and the SD card works fine but as you said, it is recognized as a USB thumb-drive.

I'm not sure if this is a 64bit exclusive bug, we should wait until someone with the 32bit version reports the same issue.

---

### Post by cybercon on 2011-06-22
i have the exact problem with SDcard reader (cannot detect) on Ubuntu 11.04 64bit installed on my Lenovo G470.

my lsusb says;

Bus 002 Device 004: ID 5986:0292 Acer, Inc 
Bus 002 Device 003: ID 09da:054f A4 Tech Co., Ltd 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0489:e00d Foxconn / Hon Hai 
Bus 001 Device 003: ID 0bda:0139 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by Amorget on 2011-07-03
I am having the same problem with the same SD Card reader.  So far nobody seems to have any ideas on how to get it working that I have found, have you found anything?

---

### Post by bojo on 2011-10-01
Same issue here - DELL XPS 15". I did read somewhere that if you put the card and reboot it will mount it and it will continue doing so but the system has to start with a card in. It did work for me but it is not a good approach. 

Does somebody know how to manually mount it?

Regards,
B

---

### Post by www.rzr.online.fr on 2011-10-16
> **cybercon said:**
> i have the exact problem with SDcard reader (cannot detect) on Ubuntu 11.04 64bit installed on my Lenovo G470.


This is fixed in 2011.10 version, else build a driver

-- 
[http://rzr.online.fr/q/lenovo](http://rzr.online.fr/q/lenovo)

---


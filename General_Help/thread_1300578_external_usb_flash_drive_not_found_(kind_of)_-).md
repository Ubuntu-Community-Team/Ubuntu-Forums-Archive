---
title: "external usb flash drive not found (kind of) :-)"
date: 2009-10-25
forum: General Help
---

### Post by yoma819 on 2009-10-25
hello all
i have an external usb flash drive in a pen that i would like to get data off!
however i cannot mount it in ubuntu!
i know it is being seen:


warwick@warwick-desktop:~$ lsusb
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 046d:c315 Logitech, Inc. Classic New Touch Keyboard
Bus 004 Device 002: ID 10c4:0004 Cygnal Integrated Products, Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 040d:6205 VIA Technologies, Inc. USB 2.0 Card Reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
warwick@warwick-desktop:~$ lsusb
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 046d:c315 Logitech, Inc. Classic New Touch Keyboard
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 040d:6205 VIA Technologies, Inc. USB 2.0 Card Reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


lsusb shows it as: Bus 004 Device 002: ID 10c4:0004 Cygnal Integrated Products, Inc. 
however it will not see that it has a partition on it!
the pen did come with windows drivers but i dont know how to use them under ubuntu!
any help please?
cheers
yoma

---

### Post by P4man on 2009-10-25
what does

```
sudo fdisk -l
```

report?
It could be one of those [dreaded u3 enabled flashdrives.]("http://en.wikipedia.org/wiki/U3") in which case you'll need a windows utility to change the firmware to make it a normal flash drive.

---

### Post by yoma819 on 2009-10-25
hi 
thanks for the reply
the output of fdisk is:
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x63ee63ee

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       48443   389118366    7  HPFS/NTFS
/dev/sda2           48444       60801    99265635    f  W95 Ext'd (LBA)
/dev/sda5           48444       60293    95185093+  83  Linux
/dev/sda6           60294       60801     4080478+  82  Linux swap / Solaris

so it does not come up!
how would i go about accessing the u3 enabled drives?
many thanks
yoma

---

### Post by P4man on 2009-10-25
well i thought u3 enabled drives did show at least something in linux, they would even show 2 partitions iirc, so im not entirely sure this is your problem. 

But if it is, then the only solution is plugging it in a windows machine and running the u3 removal utility (which will wipe all contents and irreversibly remove u3 firmware).

Can you give the brand/type of stick?

---

### Post by yoma819 on 2009-10-25
hello
thank you for your reply!
it is a memoq digial voice recorder and pen!
i am trying to recover data from it and o do this i need to have it mounted as a normal device!
do you think it is possible?
cheers
yoma

---

### Post by P4man on 2009-10-25
I guess not :(
It doesnt seem to have firmware that allows the device to work as standard usb storage device. So you'll need drivers which probably are only available for windows. at least a brief google didnt return anything useful (most of the hits were your posts lol)

You could install windows in virtualbox to use the device I guess, but other than that, I wouldnt count on it

---

### Post by yoma819 on 2009-10-25
ok thanks for your help 
much appreciated
thanks
yoma
:)

---

### Post by SPr on 2009-10-25
> 
xxxx@xxxx:~$ aptitude show u3-tool 
Package: u3-tool
New: yes
State: not installed
Version: 0.2-1
Priority: optional
Section: utils
Maintainer: Evgeni Golov <evgeni@debian.org>
Uncompressed Size: 111k
Depends: libc6 (>= 2.3.4), libusb-0.1-4 (>= 2:0.1.12)
Description: tool for controlling the special features of a U3 USB flash disk
 Tool for controlling USB flash devices that conform to the U3 specifications.
 You can do the following with your U3 flash: 
 * Replace the CD image 
 * Change the size of the virtual CD or completely remove it 
 * Enable and disable security 
 * Unlock and change the password of secured U3 device 
 * Obtain various device information
Homepage: [http://u3-tool.sourceforge.net/](http://u3-tool.sourceforge.net/)

Not used it and don't know how good it is and I can only assume it can read data from U3 flash drives. It's in a Debian repo so it may be in a Ubuntu repo.

from the web page:
> 
WARNING: This Software is still alpha. Since the commands for controlling U3 devices aren't publicly available, we don't excatly know what we are doing. Although the application has been tested on a Sandisk Cruzer micro and a Verbatim Store 'N Go, it is not said that it won't stop other devices from working. The author is not responsible for any damage to your device. 
Supported devices

In general all U3 USB flash devices should be supported. A list of U3 compatible devices can be obtained from the U3 website. 

The software is currently tested with the following drives: 
Sandisk Cruzer Micro U3 512Mb
Sandisk Cruzer Micro U3 4Gb
Verbatim Store 'N Go 1Gb
 Use at your own risk.

---

### Post by P4man on 2009-10-25
thanks, that looks interesting as the issue comes up regularly. Although its no use to the OP as its no u3 memory stick but a voice recorder.

---

### Post by SPr on 2009-10-25
LOL, I mis-understood then.

---


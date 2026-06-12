---
title: "Mounting Samsung Rant?"
date: 2010-04-06
forum: General Help
---

### Post by V_S_R on 2010-04-06
I'm trying to mount my Samsung Rant, but it doesn't seem to show up for me.

> **lsusb:**
Bus 004 Device 012: ID 05c6:1000 Qualcomm, Inc.

Does anyone know a way to get it to mount?

Thanks.

---

### Post by V_S_R on 2010-04-06
Still need help on mounting my phone :\

---

### Post by gamblor01 on 2010-04-25
What version of Ubuntu are you running?  I know for a fact that it used to work previously -- I was running 8.10 when I first got the phone and everything worked fine.  Just connect the USB cable, go to your main menu and press 0-6-1 (that's Tools -> Mass storage -> Connect to PC).

I am running 9.04 (Jaunty) and it no longer works.  There was a thread not too long ago that discussed this issue:

[http://ubuntuforums.org/showthread.php?t=1211635](http://ubuntuforums.org/showthread.php?t=1211635)


I haven't upgraded any of my systems to 9.10 yet (Karmic) but I plan on upgrading soon when Lucid is released.  Maybe this has been fixed in 9.10 or 10.04.  Good luck...

---

### Post by conradin on 2010-04-25
Plug in your phone, then try giving us the out put from:
```

lsusb

```
&
```

mount

```

---

### Post by gamblor01 on 2010-04-26
The device will show up in lsusb, but it never gets automatically mounted (and therefore never shows up in the mount output).  Here is some verbose output from lsusb:

```

bmayes@bdmlin:~$ sudo lsusb -d 05c6:1000 -v

Bus 005 Device 009: ID 05c6:1000 Qualcomm, Inc. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x05c6 Qualcomm, Inc.
  idProduct          0x1000 
  bcdDevice            0.00
  iManufacturer           1 Qualcomm, Incorporated
  iProduct                2 USB MMC Storage
  iSerial                 3 000000000002
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xc0
      Self Powered
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk (Zip)
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x05  EP 5 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
Device Status:     0x0002
  (Bus Powered)
  Remote Wakeup Enabled

```



and here is the mount ouput (which shows the same 15 lines regardless of whether or not the phone is connected or disconnected from the USB port):


```

bmayes@bdmlin:~$ mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-18-generic/volatile type tmpfs (rw,mode=755)
/dev/sda3 on /data type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/bmayes/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=bmayes)

```


In dmesg I do see this:

```

[28301.921152] usb 5-2: new full speed USB device using uhci_hcd and address 9
[28302.080035] usb 5-2: configuration #1 chosen from 1 choice
[28302.104429] usb-storage: probe of 5-2:1.0 failed with error -5

```



It looks like there is a bug report for this same error (though not specifically reporting against the Samsung Rant, it was reported for another Samsung phone and some others):

[https://bugs.launchpad.net/linux/+bug/367484](https://bugs.launchpad.net/linux/+bug/367484)


I can't reboot right now because I'm at work and need my laptop up right now, but I'm going to try the second suggestion of updating /etc/modules.  We'll see how it goes.  I'll try both suggestions later tonight if need be.

---

### Post by gamblor01 on 2010-04-26
FYI I just finished stuff up at work today so I stuck usb-storage option_zero_cd=2 in /etc/modules and rebooted.  It works!

I can read the files off of the card and write files to the card.  Seems to be working just fine.  Not sure why I never investigated this before -- guess I already had all of my music on my SD card so I didn't need to be transferring stuff any more.  Plus it works fine if I plug it into my macbook pro so if I really needed to transfer something, that worked.  But the more stuff I can get working in Linux the better.

Now if only I could get bibble 5 to run on Linux.  Maybe I could get away from Aperture and be Linux ONLY!

---

### Post by mikeymo1741 on 2010-12-05
I had the same problem in 10.04, but it mounts fine (automatically) in 10.10.

---


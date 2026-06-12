---
title: "The magically vanishing USB key"
date: 2009-09-02
forum: General Help
---

### Post by carniola on 2009-09-02
I've been having some problems with USB keys. Specifically, when I plug them in, they typically appear... then vanish... then reappear. (I have tested three different types of USB key and it happens with all three.)

This was a bit annoying but I got used to it. Now, however, they fail to appear at all... unless I plug in the key and restart the computer, which is fairly tedious.

All the keys are formatted in NTFS, because I occasionally need to plug them into Windows machines, and all three do work flawlessly in XP.

For that matter, once the flash drives actually appear in Ubuntu they work like a charm... I just need to find a way to make that happen consistently. :)

Any help would be greatly appreciated!

---

### Post by P4man on 2009-09-02
sounds like a problem with your usb controller. Can you try a different port/hub?

---

### Post by carniola on 2009-09-02
I did try using different ports -- but no success. The flash drive won't appear.

---

### Post by P4man on 2009-09-02
is it still visible in the output of 

```
lsusb
```

?

---

### Post by carniola on 2009-09-02
> Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 007: ID 059f:1027 LaCie, Ltd 
Bus 004 Device 002: ID 058f:6362 Alcor Micro Corp. Hi-Speed 21-in-1 Flash Card Reader/Writer (Internal/External)
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 050d:0131 Belkin Components Bluetooth Device with trace filter
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Aye. Thar she blows in the 2nd line. (It's a LaCie key)

---

### Post by P4man on 2009-09-02
And when you type:

```
sudo fdisk -l
```

---

### Post by carniola on 2009-09-02
That gives me this:

> Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000f193

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          18      144553+  83  Linux
/dev/sda2              19       91201   732427447+   5  Extended
/dev/sda5              19         504     3903763+  82  Linux swap / Solaris
/dev/sda6             505        1720     9767488+  83  Linux
/dev/sda7            1721       91201   718756101   83  Linux

Disk /dev/sdb: 8589 MB, 8589934080 bytes
255 heads, 63 sectors/track, 1044 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdg: 8086 MB, 8086618112 bytes
255 heads, 63 sectors/track, 983 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2c6b7369

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1               1         983     7895916    7  HPFS/NTFS



---

### Post by P4man on 2009-09-02
sdg being the usb key I imagine..

Well.. see if you can mount it ?

---

### Post by carniola on 2009-09-02
I tried creating a directory and then this:

```
sudo mount /dev/sdg
```

but it didn't work. I suspect this is the wrong code?

---

### Post by P4man on 2009-09-02
sudo mount /dev/sdg**1** /media/whateverdiryoumade

---

### Post by carniola on 2009-09-02
> mount: special device dev/sdg1 does not exist

:confused:

---

### Post by P4man on 2009-09-02
Well, it had to start going wrong somewhere :)

BTW, Im assuming you typed that, instead of a copy/paste and that the actual message mentioned **[COLOR="Red"]/[/COLOR]**dev/sdg1 right?

Have a look in dmesg if you can see something related to sdg. (system > admin > log file viewer. Look at dmesg).

Another thing to try, is delete the partition, recreate it and format the stick on ubuntu. Use partition editor in system > administration, if you dont have it, install it with:

> sudo apt-get install gparted

See if it works as long as you don't use it in windows.

For now, im guessing its either a problem with the usb controller, or possibly a virus damaging the partition...?

---

### Post by carniola on 2009-09-03
After a system restart things are suddenly normal, which is ironically a bit frustrating, since now I can no longer troubleshoot the problem... #-o 

However, it's been spotty for weeks now and I'm guessing it will start up again soon.

I'm very, very thankful for your help. You've proven again what a great community this is!

---

### Post by carniola on 2009-10-02
I think I've figured it out. The culprit seems to be [_this bug in Nautilus_]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/366262/"), in which all desktop icons suddenly and inexplicably do a Copperfield. It took me a long time to notice because I typically have no icons except for removable media...

Anyway, for anyone who stumbles across this, the workaround is just typing "nautilus" in your terminal. Removable media icons (and any other desktop icons) will then reappear.

If anyone knows of a permanent (or better) fix, I'd love to hear it!

---


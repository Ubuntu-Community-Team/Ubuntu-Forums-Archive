---
title: "Can't reinstall grub2 after installing Win7"
date: 2009-11-09
forum: General Help
---

### Post by spoon_ on 2009-11-09
I've followed the guide for reinstalling grub2 here: [http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html)

But it still just boots right into Windows. I don't get any errors during the process, it all appears to be working fine. 

Here's the output of my fdisk -l (when I boot from live CD):

```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa8dea8de

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       15271   122664276    7  HPFS/NTFS
/dev/sda2           15272       38913   189904365    5  Extended
/dev/sda5           15272       38913   189904332+   7  HPFS/NTFS

Disk /dev/sdb: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0009ae16

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1           14372       91201   617136973   83  Linux
/dev/sdb2               1       14371   115435026    5  Extended
/dev/sdb5               1         498     4000122   82  Linux swap / Solaris
/dev/sdb6             499       14371   111434841   83  Linux

Partition table entries are not in disk order

```

/dev/sdb6 is my / partition, so that's the one I mount to /mnt. Windows is installed on /dev/sda1.

I'm on Karmic 64-bit.

Anyone have any ideas? Thanks.

---

### Post by Woody1987 on 2009-11-09
Which hard drive is set to boot first in the bios? Try setting it to boot off the other drive.

---

### Post by spoon_ on 2009-11-09
> **Woody1987 said:**
> Which hard drive is set to boot first in the bios? Try setting it to boot off the other drive.

Oooh, that got me back into Ubuntu, thanks! When it boots, it shows me a grub2 screen, but I think it's still the old menu from before I installed Win7. When I installed Win7, I replaced WinXP (formatted the XP partition), and the grub2 menu that I now see includes WinXP instead of Win7. When I try to boot into this "WinXP" from grub2, I get a device error, or some such.

It seems like the new grub2 install that I made isn't being used...

---

### Post by ranch hand on 2009-11-09
Run;
```

sudo update-grub

```
Try to get your information in better places.  Check the link in my sig.  The links in that post, are to people who actually have seen grub2.  Indeed, actually use grub2.  Know how to make it sit up and beg.

The graphics aren't as cool though.

---

### Post by spoon_ on 2009-11-09
> **ranch hand said:**
> Run;
```

sudo update-grub

```
Try to get your information in better places.  Check the link in my sig.  The links in that post, are to people who actually have seen grub2.  Indeed, actually use grub2.  Know how to make it sit up and beg.

The graphics aren't as cool though.

That did it, thanks a lot!

---


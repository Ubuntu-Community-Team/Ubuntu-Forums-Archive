---
title: "GRUB error on external hard drive"
date: 2011-02-13
forum: General Help
---

### Post by michaellarsen on 2011-02-13
Alright so I'm pretty new to this whole forum thing, but i have a problem and i was wondering if anyone could help. I have a Dell Inspiron 1525 with a Western Digital 2TB external hard drive connected. On my external hard drive i have my partitions setup sdb1 is my fedora partition, where i had installed ubuntu but removed it, sdb2 is my os x partition, sdb3 is my time machine partition, and sdb4 is my misc. partition thats readable from all my operating systems. Now i have my BIOS setup so that if my external hard drive is connected it will boot from that, but when i try to boot from it theres a grub error, and im not sure how to get rid of grub without deleting everything on my external hard drive. Any help would be greatly appreciated.

---

### Post by dabl on 2011-02-13
If you intend to continue booting the external drive, you don't want to get rid of Grub, do you? You may need to reinstall it -- that's not too tough to do.

From a running Linux system (booted Ubuntu Live CD will do), and with the external drive plugged in, first ID all the hard drives:

```
sudo fdisk -lu
```

Then mount the partition where you want Grub to "connect" with -- only one of your Linuces can be the one that controls the grub menu.  Let's assume it is /dev/sdc2.  Then you would mount that partition:

```
sudo mkdir -p /mnt/SDC2
```

```
sudo mount -t ext4 /dev/sdc2 /mnt/SDC2
```

Now with the partition mounted, you have only to install grub:

```
sudo grub-install --root-directory=/mnt/SDC2 /dev/sdc
```

and you should be good to go.

---

### Post by michaellarsen on 2011-02-13
Thank you for the help, but i don't think i want GRUB anymore because it doesnt recognize the chameleon bootloader that i need to run os x on here, and I already have my sdb1 fedora 14 partition marked as the active partition, it just doesnt recognize it either.

---

### Post by dabl on 2011-02-13
I have never removed only grub, while leaving the rest of the partition table and drive untouched, but on this page it shows the use of "dd" to remove only the MBR.  That's what you want to do -- be very careful.  Personally I'd back up 100% of the data that I cared about before doing this.

[http://www.cyberciti.biz/faq/linux-how-to-uninstall-grub/](http://www.cyberciti.biz/faq/linux-how-to-uninstall-grub/)

---

### Post by bigjim01 on 2011-02-18
I have a similar problem. I am completely new to UBUNTU and Linux in general. I installed Ubuntu to an external hard drive and it runs very well and I like it. However I have decided I don't want to invest the time to learn a new system. Since I installed UBUNTU I now have the GRUB boot menu. It was defaulting to UBUNTU and I have since learned to modify GRUB to default to Windows7. So far so good.

I would like to totally get rid of UBUNTU but I want to be rid of that GRUB boot menu also. How do I uninstall UBUNTU and will that action also wipe out the reference to GRUB? I could simply format the external drive and wipe it out but I'm afraid that would not remove the boot menu.

I would appreciate any help.

---


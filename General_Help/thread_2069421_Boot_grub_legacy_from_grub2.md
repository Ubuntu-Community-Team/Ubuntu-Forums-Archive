---
title: "Boot grub legacy from grub2?"
date: 2012-10-10
forum: General Help
---

### Post by someoney3000 on 2012-10-10
I have an old hard disk drive (the ribbon one) that I see using usb has a boot partition but don't see anything else.

So, I thought to try to boot up the the disk (which is running legacy grub) over usb from grub2 to check it out.

But, google has failed me.  I can find the drive fine, I think.

```

grub> ls (hd1,1)
Partition hd1,1: Filesystem type ext2 - Label "/boot" blah blah blah
grub> set root=(hd1,1)
grub> chainloader +1
error: invalid signature
grub> NOOOOOOOOOOOOOO!

```I want to see the data on that disk.  Is there a way to boot it?

---

### Post by ajgreeny on 2012-10-10
Not quite sure exactly what you mean by "the ribbon one" but perhaps it is a pata or IDE attached drive on a ribbon cable.

If you can see it has a boot partition when it's attached by usb (in a caddy?) you should also be able to see what other partitions may be on it with the command ```
sudo fdisk -l
```Once that can be seen it should be possible to mount the partitions and get off any data on the drive quite easily. You can even do it with a live CD session if there is no other way.

---

### Post by oldfred on 2012-10-10
[LEFT]Even with grub legacy most users did not install it to a PBR or partition boot sector. Your chainload would only work if grub was in PBR. Grub legacy also is normally in the MBR, has part of the boot code in the sectors just after the MBR to find the partition with the boot code.

If USB is bootable.

I used to use an entry like this. Boot drive is always hd0, then on my system the grub2 drive order is the same as the ports plugged into the SATA ports on hard drive. But USB flash drives can change that order.

menuentry "Lucid Lynx on sda (When from sdc) Chainboot" {
set root=(hd1)
chainloader +1
}

[/LEFT]

---

### Post by someoney3000 on 2012-10-17
> **ajgreeny said:**
> Not quite sure exactly what you mean by "the ribbon one" but perhaps it is a pata or IDE attached drive on a ribbon cable.

If you can see it has a boot partition when it's attached by usb (in a caddy?) you should also be able to see what other partitions may be on it with the command ```
sudo fdisk -l
```Once that can be seen it should be possible to mount the partitions and get off any data on the drive quite easily. You can even do it with a live CD session if there is no other way.

Alright this helped immensely.

What I did:

I identified the partition I wanted to mount via:
sudo fdisk -l

Turns out it is a LVM partition so, I installed lvm2 and then
vgscan vgchange -a y

The end!

Thanks for all the helps guys!

---


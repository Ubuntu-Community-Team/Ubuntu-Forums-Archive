---
title: "ubuntu, geexbox, grub2 configuration"
date: 2009-12-09
forum: General Help
---

### Post by jdcnosse on 2009-12-09
Okay, so I was reading someone's post on how to edit the grub2 configuration files (since they're different from grub-legacy), and I still can't seem to get it to work.  The partition I want to add isn't actually used in ubuntu (it's geexbox, but it is formatted as ext3).  I put the geexbox entry in the 40_custom file, as the tutorial said to.

```

#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "GeeXboX" {
set root=(hd0,2)
linux /vmlinux root=/dev/sda2
initrd /initrd.gz
}

```

Here's the output of my fdisk -l

```

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         851     6835626   83  Linux
/dev/sda2             852         973      979965   83  Linux
/dev/sda3             974        9483    68356575   83  Linux
/dev/sda4            9484        9729     1975995   82  Linux swap / Solaris


```

sda1 is ubuntu, sda2 is geexbox, sda3 is /home on ubuntu, and sda4 is obviously my swap partition.

---

### Post by Jose Catre-Vandis on 2010-01-30
I take it you have installed GeexBox to the hard drive partition.

You'll need to point grub2 at the GEEXBOX directory. Here is my grub2 entry
(although I "didn't" install Geexbox, just copied the GEEXBOX directory over onto my data partition.

```
menuentry "Geexbox HDD" {
        set root=(hd0,8)
        linux /GEEXBOX/boot/vmlinuz root=/dev/ram0 rw rdinit=linuxrc boot=UUID=1d2b639a-b83f-46f3-8a04-3f647fcce2af lang=en remote=atiusb receiver=atiusb keymap=qwerty splash=silent video=vesafb:ywrap,mtrr quiet
        initrd /GEEXBOX/boot/initrd.gz
```

You will need the UUID for your partition. Run
```
sudo blkid
```
to get the right number

---

### Post by irw on 2010-02-07
.

---

### Post by Jose Catre-Vandis on 2010-02-07
> **irw said:**
> a note on disk / partition numbers:
your Geexbox partition is sda2, but you have root as (hd0,2) - this should be (hd0,1)

sda1 = hd0,0
sda2 = hd0,1
etc.

(I realise the OP was a long time ago, so he probably has it sorted, but for anyone else who comes across this ...)

Ian

The above is right for legacy grub, but not for grub2, where hdX,X and sdXX numbers match.

---


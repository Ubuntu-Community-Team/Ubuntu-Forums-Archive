---
title: "unable to add ubuntu to opensolaris grub"
date: 2009-10-24
forum: General Help
---

### Post by zerobotman on 2009-10-24
i've had ubuntu on my laptop for some time but since my college course uses an altera de1 fpga i had to install drivers which do not work well in ubuntu. i have a windows partition but i never use it for anything since it's really buggy for some reason and i don't want to put anything of importance on it. since the altera de1 came with solaris drivers i figured i would give opensolaris a try. unfortunately i must have selected (if i even had the option) to install it's grub bootloader and now i can't seem to find the right partition to add to the menu.lst. after reading this little blerb in menu.lst

> # Unknown partition of type 5 found on /dev/rdsk/c8d0p0 partition: 2
# It maps to the GRUB device: (hd0,1) .i added this 

> title Ubuntu
    rootnoverify (hd0,1)
    chainloader +1to make the final menu.lst look like this

>  splashimage /boot/grub/splash.xpm.gz
background 215ECA
timeout 30
default 0
#---------- ADDED BY BOOTADM - DO NOT EDIT ----------
title OpenSolaris 2009.06
findroot (pool_rpool,2,a)
bootfs rpool/ROOT/opensolaris
splashimage /boot/solaris.xpm
foreground d25f00
background 115d93
kernel$ /platform/i86pc/kernel/$ISADIR/unix -B $ZFS-BOOTFS,console=graphics
module$ /platform/i86pc/$ISADIR/boot_archive
#---------------------END BOOTADM--------------------

title Windows
    rootnoverify (hd0,0)
    chainloader +1
title Ubuntu
    rootnoverify (hd0,2)
    chainloader +1


# Unknown partition of type 5 found on /dev/rdsk/c8d0p0 partition: 2
# It maps to the GRUB device: (hd0,1) . 

but it doesn't seem to work. i've tried hd0,1 and hd0,3 as well.

---

### Post by dc5219 on 2010-05-01
You could try removing the comments (#)

---

### Post by WorMzy on 2010-05-01
That is an awful suggestion, dc.

Try this: 
```

title        Ubuntu
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.32-21-generic root=UUID=[COLOR=Red]<INSERT PARTITION UUID HERE> [/COLOR]ro quiet
initrd        /boot/initrd.img-2.6.32-21-generic
savedefault
boot
```

---

### Post by ankspo71 on 2010-05-01
Are you using ext4 for Ubuntu? Don't quote me on this but I think OpenSolaris can't read ext4 partitions (yet).
Borrowed from this forum post dated in 2009 [http://opensolaris.org/jive/thread.jspa?messageID=441462](http://opensolaris.org/jive/thread.jspa?messageID=441462)

If you would like to try using Grub from Ubuntu, you can follow the tutorials found here [https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---


---
title: "usplash not working correctly"
date: 2009-08-14
forum: General Help
---

### Post by joebob213 on 2009-08-14
Hello all.  Yesterday I converted my Ubuntu 9.04 OS to Ubuntu Studio via: [https://help.ubuntu.com/community/UbuntuStudio/UpgradingFromHardy](https://help.ubuntu.com/community/UbuntuStudio/UpgradingFromHardy)

Everything works correctly except when I boot I get text instead of the pretty UBUNTU STUDIO status bar!  Not a big deal but it is an annoyance and I would like to get it working.  Ideas?  What outputs do I need to post?

---

### Post by soapBAR2 on 2009-08-14
In your /boot/grub/menu.lst (or when you're booting, the grub menu), there's a line called "kernel". At the end of the line for the kernel you're booting, put "splash".

Here's what mine looks like:

> title           Ubuntu 9.04, kernel 2.6.28-14-generic
root            (hd0,2)
kernel          /vmlinuz-2.6.28-14-generic root=/dev/md1 ro quiet splash
initrd          /initrd.img-2.6.28-14-generic

title           Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
root            (hd0,2)
kernel          /vmlinuz-2.6.28-14-generic root=/dev/md1 ro  single
initrd          /initrd.img-2.6.28-14-generi

The second one is for recovery mode.

---

### Post by joebob213 on 2009-08-14
Thank you but that was actually the first thing I checked :(  Here's what mine looks like: 

```
title		Ubuntu 9.04, kernel 2.6.28-14-generic
uuid		b9fa0e3e-9af9-4c8f-849a-862a4c517192
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=b9fa0e3e-9af9-4c8f-849a-862a4c517192 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-14-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid		b9fa0e3e-9af9-4c8f-849a-862a4c517192
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=b9fa0e3e-9af9-4c8f-849a-862a4c517192 ro xforcevesa  single
initrd		/boot/initrd.img-2.6.28-14-generic

title		Ubuntu 9.04, memtest86+
uuid		b9fa0e3e-9af9-4c8f-849a-862a4c517192
kernel		/boot/memtest86+.bin
quiet

```

Let me add that the splash comes up showing  "ubuntu studio" with a white square scrolling back and forth but when the status bar should load it drops to text mode.  I changed the theme back to the standard ubuntu theme and I get the same thing. The last time I installed Ubuntu Studio the white started at the left of the letters and filled them up as the OS loaded.  Now I get text.

---

### Post by joebob213 on 2009-08-14
Ok, I've done some more searching and it seems this is a common problem with UUID's not matching up.  Here are the outputs from from the following files:

/etc/initramfs-tools/conf.d/resume:

```
RESUME=UUID=93a76491-b5c1-4ad7-8b87-5e704a260e37
```

sudo blkid:

```
/dev/sda1: UUID="b9fa0e3e-9af9-4c8f-849a-862a4c517192" TYPE="ext4" 
/dev/sda5: TYPE="swap" UUID="93a76491-b5c1-4ad7-8b87-5e704a260e37" 
/dev/sdb2: UUID="F044-9137" TYPE="vfat" 
/dev/sda2: UUID="34E4CEBCE4CE7F9A" TYPE="ntfs" 
/dev/sda4: UUID="9c810547-4299-42bc-8b11-0111d471298b" SEC_TYPE="ext2" TYPE="ext3" 

```

/etc/fstab:

```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                    0  0  
# / was on /dev/sda1 during installation
UUID=b9fa0e3e-9af9-4c8f-849a-862a4c517192  /              ext4         relatime,errors=remount-ro  0  1  
# swap was on /dev/sda5 during installation
UUID=93a76491-b5c1-4ad7-8b87-5e704a260e37  none           swap         sw                          0  0  
/dev/scd1                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8       0  0  
/dev/sdb2                                  /media/sdb2    vfat         gid=121,users               0  0  
/dev/sda3                                  /media/sda3    ntfs         defaults                    0  0  
```

Looks to me like all swap UUID's match up?  They didn't but I changed fstab and resume after some reading.  Still doesn't work :(

---

### Post by plucky on 2009-08-14
> Looks to me like all swap UUID's match up? They didn't but I changed fstab and resume after some reading. Still doesn't work 


Did you update initramfs after you changed the UUIDs'? ```
sudo update-initramfs -u -k all
```


Also please post output of ```
sudo fdisk -l
``` .What does /dev/sda4 have on it as it is not mentioned in /etc/fstab?

Good luck

---


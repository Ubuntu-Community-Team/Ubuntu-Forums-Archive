---
title: "Clonezilla HDD install corrupts grub?"
date: 2012-07-23
forum: General Help
---

### Post by D0natell0 on 2012-07-23
Hi, following previous successful use of clonezilla live on a usb stick, I decided to try creating a recovery partition on my hard-drive.

So, I attempted to follow the solution for adding Clonezilla to a separate  partition on my HDD (as at clonezilla.org/livehd.php) but somethings  messed up somewhere. 

Now when I try to boot, there's no grub prompt, it goes straight(!) to  Clonezilla but this is broken!! It's looking for the directory "live",  which was renamed "live-hd", as per the instructions.  

I'm running Ubuntu 8.04 (on /dev/sda1) with legacy grub and clonezilla  1.2.12-67 is on /dev/sda3. 

Why is it there's no grub prompt? Why does it boot straight to  Clonezilla?
:confused:
It seems that *maybe* the boot sector has become corrupt. Maybe it's due  to a restriction on length of entries in "/boot/grub/menu.lst"? 

Here's the excerpts from my grub menu.lst: 
```

title             Ubuntu 8.04.4 LTS, kernel 2.6.24-32-generic 
root             (hd0,0) 
kernel          /boot/vmlinuz-2.6.24-32-generic  root=UUID=18e08f49-681b-495b-8fa6-55bfbd534918 ro quiet splash 
initrd            /boot/initrd.img-2.6.24-32-generic 
quiet  

``````

title              Clonezilla live on harddrive 
root               (hd0,3) 
kernel            /live-hd/vmlinuz boot=live live-config noswap nolocales edd=on  nomodeset ocs_live_run="ocs-live-general" ocs_live_extra_param=""  ocs_live_keymap="" ocs_live_batch="no" ocs_lang="" vga=788 ip=frommedia  nosplash live-media-path=/live-hd bootfrom=/dev/sda3  toram=filesystem.squashfs  
initrd /live-hd/initrd.img 
boot 

```Any help gratefully received ;)

---

### Post by D0natell0 on 2012-07-23
Would it be a fair guess to say that the last line in the second code excerpt from "/boot/grub/menu.lst" needs modified? (i.e. is "boot" a switch that means the OS will always boot from this setting?)

Any thoughts?

---

### Post by D0natell0 on 2012-07-24
I ran a boot repair disk and generated a boot info log. Here's a piece of that:

```

sda3: __________________________________________________________________________ 

     File system:       vfat     Boot sector type:  FAT32     Boot sector info:  According to the info in the boot sector, sda3 starts                         at sector 0. But according to the info from fdisk,                         sda3 starts at sector 51838976.     Operating System:       Boot files:        /syslinux/syslinux.cfg


```The full log is at:
[http://paste.ubuntu.com/1108454/](http://paste.ubuntu.com/1108454/)

Can anyone shed any light?
[-o<

---

### Post by D0natell0 on 2012-07-25
bump

---


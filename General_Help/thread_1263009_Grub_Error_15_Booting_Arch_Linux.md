---
title: "Grub Error 15 Booting Arch Linux"
date: 2009-09-10
forum: General Help
---

### Post by Penguin Guy on 2009-09-10
I switched from using a UUID to using the standard (hd0,0) method. Everything now works, thanks to those who helped.

**[[COLOR="Red"]/boot/grub/menu.lst[/COLOR]]**
[PHP]
# Arch Linux
title		Utility
uuid		05c939ed-7fbb-4abc-a0c5-fa54eef6f85e
kernel		/boot/vmlinuz26 ro single vga=794
#kernel		/boot/vmlinuz26 root=UUID=05c939ed-7fbb-4abc-a0c5-fa54eef6f85e ro single vga=794
initrd		/boot/kernel26.img
[/PHP]

**[[COLOR="Green"]/boot/grub/menu.lst[/COLOR]]**
[PHP]
# Arch Linux
title		Utility
root		(hd0,7)
kernel		/boot/vmlinuz26 ro single vga=794
initrd		/boot/kernel26.img
[/PHP]


**$ blkid (edited for readability)**
[PHP]/dev/loop0:                                                            TYPE="squashfs" 
/dev/sda1: LABEL="Windows" UUID="5C1886B518868E28"                     TYPE="ntfs" 
/dev/sda5: LABEL="/boot"   UUID="33954389-0a03-4822-96c4-c6e5924de048" TYPE="ext3" SEC_TYPE="ext2" 
/dev/sda6: LABEL="/"       UUID="44549c7f-d040-4322-ae8c-c48ae0713952" TYPE="ext3" 
/dev/sda7: LABEL="/home"   UUID="0755623d-8456-4602-9bbc-b9b19f5ad5b2" TYPE="ext3" SEC_TYPE="ext2" 
/dev/sda8: LABEL="Utility" UUID="05c939ed-7fbb-4abc-a0c5-fa54eef6f85e" TYPE="ext3" SEC_TYPE="ext2" [/PHP]


**$ ls /media/Utility/boot**
```
grub  kernel26-fallback.img  kernel26.img  System.map26  vmlinuz26
```

---

### Post by bobnutfield on 2009-09-10
Hello,

You normally get this error when the kernel file is not identified correctly as it is in the /boot file for the partition you are trying to boot, in this case it is shown as:

> /boot/vmlinuz26 ro single vga=794

Mount that partition from Ubuntu and make sure you do not have either a typo in the vmlinuz title or a missing symlink.

---

### Post by nikhilbhardwaj on 2009-09-10
the arch kernel ie vmlinuz26 and ubuntu's kernel are in the same folder ie a seperate /boot are they

then you need to replace 
/boot/vmlinuz26
with /vmlinuz26

---

### Post by Penguin Guy on 2009-09-10
> **bobnutfield said:**
> Hello,

You normally get this error when the kernel file is not identified correctly as it is in the /boot file for the partition you are trying to boot, in this case it is shown as:



Mount that partition from Ubuntu and make sure you do not have either a typo in the vmlinuz title or a missing symlink.
I assumed that I didn't need a symlink to vmlinuz otherwise it would already be there. I am quite sure I haven't made a typo though:

**$ ls /media/Utility/boot**
```
grub  kernel26-fallback.img  kernel26.img  System.map26  vmlinuz26
```

> **nikhilbhardwaj said:**
> the arch kernel ie vmlinuz26 and ubuntu's kernel are in the same folder ie a seperate /boot are they

then you need to replace 
/boot/vmlinuz26
with /vmlinuz26

It is all on one partition if that's what you mean.

---

### Post by Penguin Guy on 2009-09-11
Bump.

---

### Post by Penguin Guy on 2009-09-16
Bump.

---

### Post by oldfred on 2009-09-16
I am not familiar with Arch but I think one solution is to convert to chainbooting. The disadvantage is you have to always go thru another menu, but any updates to Arch will be reflected in that menu and not require manual editing of the initial boot menu.lst.

You would have to add a Grub entry to the sda8 partition and then add a chainboot entry to that partition in your current menu.lst. You will have to check that your menu.lst in Arch is correct initially.

More info.
boot 145 systems
[http://www.justlinux.com/forum/showthread.php?p=861282#post861282](http://www.justlinux.com/forum/showthread.php?p=861282#post861282)

---

### Post by Penguin Guy on 2009-09-17
Thanks for the reply, but I would rather not do that because:
[LIST=A]
[*]As you stated, I would have to go through a second menu and
[*]It might not work anyway since grub can't find the kernel
[/LIST]

---

### Post by tjwoosta on 2009-09-18
Im not really familiar with ubuntu's grub but this is what arch's grub entry looks like on my machine

```

title  Arch Linux
root   (hd0,2)
kernel /boot/vmlinuz26 root=/dev/disk/by-uuid/9a7a347f-83cc-455d-a4d8-3dadce1e52d0 ro
initrd /boot/kernel26.img

```

maybe try useing root (hd0,?) instead of uuid ?

with grub /dev/sda1 would be hd0,0 and /dev/sda2 would be hd0,1 etc...

or maybe try removing the /boot from infront of vmlinuz26 since your ubuntu entry doesn't seem to have one ?

EDIT: just curious where are your sda2 through sda4 ?

sudo fdisk -l should list all partitions and drives

---

### Post by Penguin Guy on 2009-09-18
> **tjwoosta said:**
> Im not really familiar with ubuntu's grub
It's exactly the same as Arch's grub, and, for that matter, all other distro's grub.
> **tjwoosta said:**
> Incorrect.
Sorry, should have double-checked before posting.

> **tjwoosta said:**
> or maybe try removing the /boot from infront of vmlinuz26 since your ubuntu entry doesn't seem to have one ?
My Ubuntu entry doesn't have one because it tells grub that the file is at 'UUID=xxx/vmlinuz' which translates as 'sda5/vmlinuz' - since sda5 is my boot partition it again translates as '/boot/vmlinuz'. This is not the case with my Arch installation - it is all on one partition.

> **tjwoosta said:**
> EDIT: just curious where are your sda2 through sda4 ?
It's because sda1 through sda4 are reserved for primary partitions (that means you're only allowed four of them :(), and sda5 through everything else is reserved for logical partitions (you can have as many as you like :P).

> **tjwoosta said:**
> maybe try useing root (hd0,?) instead of uuid ?
Thanks, that worked!

[/boot/grub/menu.lst]
[PHP]# Arch Linux
title		Utility
root		(hd0,7)
kernel		/boot/vmlinuz26 ro single vga=794
initrd		/boot/kernel26.img[/PHP]

I'm still not sure why the UUID method didn't work though... :(

---

### Post by tjwoosta on 2009-09-18
Every distros grub is not always exactly the same, they sometimes do things a bit different hence the reason UUID didnt work and root did. I ran into the same sort of issues before when dual booting opensuse with ubuntu and with dual booting gentoo with arch.

---

### Post by tjwoosta on 2009-09-18
double post removed

---


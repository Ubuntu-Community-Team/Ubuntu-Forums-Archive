---
title: "Adding Xubuntu 9.10 to grub"
date: 2010-01-07
forum: General Help
---

### Post by operative.terminus on 2010-01-07
Hello,

I've installed Xubuntu 9.10 on sda2, and Chakra on sda6. I was hoping Chakra's grub would notice my Xubuntu installation, but no such luck. I would like to add my Xubuntu install to the grub menu.lst that Chakra installed. Can anyone help me with that?

---

### Post by Tim Sharitt on 2010-01-08
First, you'll need to know the file names for the kernel and initrd image files. You will find these files in the /boot directory of the xubuntu partition.

These are examples from my machine. Yours should be similar, possibly with different version numbers.
kernel:
/boot/vmlinuz-2.6.31-17-generic
initrd:
/boot/initrd.img-2.6.28-17-generic

When you have this information, you will need to open Chakra's menu.lst file for editing as root (using sudo, or kdesu with your preferred editor).

Now use the information you gathered earlier to create an entry for Xubuntu similar to the following:
```

title		Xubuntu
root            (hd0,1)
kernel		/boot/vmlinuz-2.6.28-17-generic root=(hd0,1) ro  single
initrd		/boot/initrd.img-2.6.28-17-generic
```

This example would boot kernel version 2.6.28-17-generic from the second partition on the first hard drive. You will need to adjust the file names and root to match your configuration (though hd0,1 should work since you have Xubuntu installed to /dev/sda2)

---

### Post by operative.terminus on 2010-01-08
Thanks for your reply,Tim. 

The problem I am having now is that I can't mount the Xubuntu partition to have a look at what those files say. I tried this:

```
mount /dev/sda2 /mnt/sda2
```

I'm probably doing something wrong there. 

I went ahead and added your code to Chakra's menu.lst, and tried a few variations as well, but all I get from grub is "file not found". 

If I could just get into sda2...

---

### Post by Leppie on 2010-01-08
normally you need root permissions to mount a partition.

it's best to re-install karmic's grub2 to the mbr.
boot with the karmic livecd.
in a terminal issue these commands:
```
sudo mount /dev/sda2 /mnt
sudo --recheck grub-install --root-directory=/mnt /dev/sda
```

reboot and boot into karmic, then issue this command to update your grub2 configuration file:
```
sudo update-grub
```

the os-prober should detect and add the os's installed after karmic.

---

### Post by operative.terminus on 2010-01-09
> **Leppie said:**
> 
in a terminal issue these commands:
```
sudo mount /dev/sda2 /mnt
sudo --recheck grub-install --root-directory=/mnt /dev/sda
```


When I issued the second command I got this. 

```
sudo: invalid option -- '-'
```

---

### Post by Leppie on 2010-01-09
I am terribly sorry, it should've been like this:
```
sudo mount /dev/sda2 /mnt
sudo grub-install --recheck --root-directory=/mnt /dev/sda
```

---

### Post by operative.terminus on 2010-01-09
> **Leppie said:**
> I am terribly sorry, it should've been like this:
```
sudo mount /dev/sda2 /mnt
sudo grub-install --recheck --root-directory=/mnt /dev/sda
```

No problem :) So, I tried it and it worked, adding an arch entry to grub.cfg, but now I can only boot into Xubuntu. The Arch entry is there, but when I choose it I get the message "error: you need to load the kernel first". 

My new grub.cfg looks like this:

```
### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set f2e6fe4d-db55-4b2a-9ff3-c0769c615497
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=f2e6fe4d-db55-4b2a-9ff3-c0769c615497 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set f2e6fe4d-db55-4b2a-9ff3-c0769c615497
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=f2e6fe4d-db55-4b2a-9ff3-c0769c615497 ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Arch Linux (on /dev/sda5)" {
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 4e5690eb-0c1f-47d5-95b9-f4aa76e5f8fd
	linux /boot/vmlinuz26 resume=/dev/disk/by-uuid/d34590ae-7ddc-4ee2-a79c-36877a0a95a9 root=/dev/disk/by-uuid/4e5690eb-0c1f-47d5-95b9-f4aa76e5f8fd ro
	initrd /boot/kernel26.img
}
menuentry "Arch Linux Fallback (on /dev/sda5)" {
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 4e5690eb-0c1f-47d5-95b9-f4aa76e5f8fd
	linux /boot/vmlinuz26 resume=/dev/disk/by-uuid/d34590ae-7ddc-4ee2-a79c-36877a0a95a9 root=/dev/disk/by-uuid/4e5690eb-0c1f-47d5-95b9-f4aa76e5f8fd ro
	initrd /boot/kernel26-fallback.img

```

I think this must have something to do with using separate boot partitions. My full partition table is like this:

sda1 Extended
  sda5 Chakra root ext4
  sda6 Chakra boot ext2
sda2 Xubuntu root  ext4
sda3 Swap
sda4 Home          ext3

---

### Post by Leppie on 2010-01-09
could you post the output of blkid:
```
sudo blkid
```

---

### Post by Leppie on 2010-01-09
i don't understand why the arch entries have the "resume=" kernel option. did you put it to hibernate before booting into ubuntu?

---

### Post by operative.terminus on 2010-01-09
> **Leppie said:**
> could you post the output of blkid:
```
sudo blkid
```

```
/dev/sda2: UUID="f2e6fe4d-db55-4b2a-9ff3-c0769c615497" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda3: UUID="d34590ae-7ddc-4ee2-a79c-36877a0a95a9" TYPE="swap" 
/dev/sda4: UUID="1cf7f4b2-6c63-4012-93fa-f2c1b30cb063" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="4e5690eb-0c1f-47d5-95b9-f4aa76e5f8fd" TYPE="ext4" 
/dev/sda6: UUID="093ef95c-07a3-43a7-bd8c-edc313c29dab" TYPE="ext2" 

```

---

### Post by Leppie on 2010-01-09
i think the swap contains/contained an arch hibernation image (but i could be wrong about this).
remove the resume kernel option from the 2 arch entries. open grub.cfg (yes, i know they warn you to not edit it manually):
```
gksudo gedit /boot/grub/grub.cfg
```
edit the entries:
```
menuentry "Arch Linux (on /dev/sda5)" {
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 4e5690eb-0c1f-47d5-95b9-f4aa76e5f8fd
	linux /boot/vmlinuz26 root=/dev/disk/by-uuid/4e5690eb-0c1f-47d5-95b9-f4aa76e5f8fd ro
	initrd /boot/kernel26.img
}
menuentry "Arch Linux Fallback (on /dev/sda5)" {
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 4e5690eb-0c1f-47d5-95b9-f4aa76e5f8fd
	linux /boot/vmlinuz26 root=/dev/disk/by-uuid/4e5690eb-0c1f-47d5-95b9-f4aa76e5f8fd ro
	initrd /boot/kernel26-fallback.img
```
save and exit.
try booting chakra.

---

### Post by operative.terminus on 2010-01-09
Never mind, we can call the search off. My Xubuntu installation was vanilla, straight off the live cd. The grub version must have been an older one, because while I was waiting for your response I went ahead and did a full system update and there must have been a grub update somewhere in there because now I can boot into both distros. 

As for your question, I didn't put it into hibernate. Chakra is still in alpha and there are still a lot of bugs, so strange happenings like that don't really surprise me. Even so, it is shaping up to be a great distro (or "distrolet", as they call it). 

Thank you so much for all your help. I'm glad to have both of them up and running now. :D

---

### Post by Leppie on 2010-01-09
that's excellent.
you'll get to like grub2 after a little bit, it's easier to understand than it may appear at start ;)

---


---
title: "Help to remove old kernels"
date: 2010-06-12
forum: General Help
---

### Post by giorgio.p on 2010-06-12
I have a very long list in my grub menu.
If I do an update-grub here is the list of images (which is the same as displayed by the grub menu:

george@geolaptop:/boot$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
Found linux image: /boot/vmlinuz-2.6.31-19-generic
Found initrd image: /boot/initrd.img-2.6.31-19-generic
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Dell Utility Partition on /dev/sda1
Found Microsoft Windows XP Professional on /dev/sda2
Found Microsoft Windows XP Embedded on /dev/sda5
done

My grub version is:
george@geolaptop:/boot$ grub-install -v
grub-install (GNU GRUB 1.98-1ubuntu5)

I want to remove the old kernels but they dont appear in synaptic and they dont appear to be found by apt-get. For example the output of a sample apt-get remove is here:

george@geolaptop:/boot$ sudo apt-get remove linux-image-2.6.31-14-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-image-2.6.31-14-generic

I dont really understand what is going on .. how come grub finds all those kernels and Synaptic/apt-get do not?

All the posts I have read just say remove old kernels with Synaptic... but I cant!

Any thoughts appreciated.
Cheers
George

---

### Post by clhsharky on 2010-06-12
giorgio.p

In Synaptic click on status>installed then search linux.


Sharky

---

### Post by waynefoutz on 2010-06-12
Whatever you do, don't try using wildcards in the terminal. I did that and deleted them all, including the one I was using.

---

### Post by drs305 on 2010-06-12
You can also try a great little app called Ubuntu-Tweak. Take a look at the section "Removing Older Kernels" in this post:
[http://ubuntuforums.org/showthread.php?t=818177]("http://ubuntuforums.org/showthread.php?t=818177")

You may also want to take a look at the contents of /boot/grub/grub.cfg and see if the kernels are located in the 10_linux section or in the 30_os-prober section. It could be picking up the older kernels from an old menu.lst or grub.cfg on another partition. You have 2.6.31 kernels which may be on a separate karmic partition.

---

### Post by giorgio.p on 2010-06-12
> In Synaptic click on status>installed then search linux.


It only shows the last two kernels not the dozens found by grub.

---

### Post by giorgio.p on 2010-06-12
> You can also try a great little app called Ubuntu-Tweak

Already tried that. It only shows one previous version.

---

### Post by giorgio.p on 2010-06-12
> You may also want to take a look at the contents of /boot/grub/grub.cfg and see if the kernels are located in the 10_linux section or in the 30_os-prober section

Here are the relevent bits of grub.cfg:

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 152e0437-33f4-4bac-9435-d9bba351bfc3
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=152e0437-33f4-4bac-9435-d9bba351bfc3 ro  splash quiet vga=795  quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 152e0437-33f4-4bac-9435-d9bba351bfc3
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=152e0437-33f4-4bac-9435-d9bba351bfc3 ro single  splash quiet vga=795
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 152e0437-33f4-4bac-9435-d9bba351bfc3
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=152e0437-33f4-4bac-9435-d9bba351bfc3 ro  splash quiet vga=795  quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 152e0437-33f4-4bac-9435-d9bba351bfc3
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=152e0437-33f4-4bac-9435-d9bba351bfc3 ro single  splash quiet vga=795
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 152e0437-33f4-4bac-9435-d9bba351bfc3
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=152e0437-33f4-4bac-9435-d9bba351bfc3 ro  splash quiet vga=795  quiet splash
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 152e0437-33f4-4bac-9435-d9bba351bfc3
	echo	'Loading Linux 2.6.31-20-generic ...'
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=152e0437-33f4-4bac-9435-d9bba351bfc3 ro single  splash quiet vga=795
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-19-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 152e0437-33f4-4bac-9435-d9bba351bfc3
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=152e0437-33f4-4bac-9435-d9bba351bfc3 ro  splash quiet vga=795  quiet splash
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-19-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 152e0437-33f4-4bac-9435-d9bba351bfc3
	echo	'Loading Linux 2.6.31-19-generic ...'
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=152e0437-33f4-4bac-9435-d9bba351bfc3 ro single  splash quiet vga=795
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-17-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 152e0437-33f4-4bac-9435-d9bba351bfc3
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=152e0437-33f4-4bac-9435-d9bba351bfc3 ro  splash quiet vga=795  quiet splash
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-17-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 152e0437-33f4-4bac-9435-d9bba351bfc3
	echo	'Loading Linux 2.6.31-17-generic ...'
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=152e0437-33f4-4bac-9435-d9bba351bfc3 ro single  splash quiet vga=795
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-16-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 152e0437-33f4-4bac-9435-d9bba351bfc3
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=152e0437-33f4-4bac-9435-d9bba351bfc3 ro  splash quiet vga=795  quiet splash
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-16-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 152e0437-33f4-4bac-9435-d9bba351bfc3
	echo	'Loading Linux 2.6.31-16-generic ...'
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=152e0437-33f4-4bac-9435-d9bba351bfc3 ro single  splash quiet vga=795
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-15-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 152e0437-33f4-4bac-9435-d9bba351bfc3
	linux	/boot/vmlinuz-2.6.31-15-generic root=UUID=152e0437-33f4-4bac-9435-d9bba351bfc3 ro  splash quiet vga=795  quiet splash
	initrd	/boot/initrd.img-2.6.31-15-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-15-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 152e0437-33f4-4bac-9435-d9bba351bfc3
	echo	'Loading Linux 2.6.31-15-generic ...'
	linux	/boot/vmlinuz-2.6.31-15-generic root=UUID=152e0437-33f4-4bac-9435-d9bba351bfc3 ro single  splash quiet vga=795
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-15-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 152e0437-33f4-4bac-9435-d9bba351bfc3
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=152e0437-33f4-4bac-9435-d9bba351bfc3 ro  splash quiet vga=795  quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 152e0437-33f4-4bac-9435-d9bba351bfc3
	echo	'Loading Linux 2.6.31-14-generic ...'
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=152e0437-33f4-4bac-9435-d9bba351bfc3 ro single  splash quiet vga=795
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 152e0437-33f4-4bac-9435-d9bba351bfc3
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 152e0437-33f4-4bac-9435-d9bba351bfc3
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Dell Utility Partition (on /dev/sda1)" {
	insmod fat
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 07d7-0209
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Microsoft Windows XP Professional (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 84bc64eebc64dc64
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Microsoft Windows XP Embedded (on /dev/sda5)" {
	insmod fat
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 07d7-0209
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

---

### Post by cbowman57 on 2010-06-12
Go into the /boot directory and delete all the kernel entries that you don't want.  There are a couple files that aren't redundant, leave them alone.  Go into your /lib/modules directory and delete the directories that don't correspond to the kernel you want to keep (also /lib64/modules if appropriate).

Run 'sudo update-grub' that should take care of it.  Make sure that you don't delete anything related to the working kernel, i.e. initrd.img files, system.map, etc..

As an example 

 If I wanted to delete the generic kernel I would delete the following:

abi-2.6.34-020634-generic
config-2.6.34-020634-generic      
System.map-2.6.34-020634-generic
initrd.img-2.6.34-020634-generic

---

### Post by giorgio.p on 2010-06-13
Thanks to cbowman57.
I deleted the unwanted ones from /boot
/lib/modules only contained the last two versions.

Then I did another grub-update and the grub menu is vastly reduced.

Cheers
George

---

### Post by pikamoku on 2010-06-13
maybe you have already solved your problem but:

**run in terminal**
```
uname -r
``` 
to get the kernel you are using. Then:

```
dpkg --get-selections | grep linux-image
```

to know what kernel(s) **you want** to remove. Usually all but the last one.

and then

```
sudo aptitude purge "old-kernel-entry"
```

to remove (purge) the-old-kernel.

be aware of not removing the **"linux-image-generic"** entry. Repeat this with all the kernels you want to remove.

**Update:**
I'm using burg instead of grub. With these instructions **grub** update automaticaly, but not burg. To avoid this, and get **burg** updated do in terminal:
```
sudo mv /usr/sbin/update-grub /usr/sbin/update-grub.bak
``` 
for security reasons, and then:
```
sudo ln -s /usr/sbin/update-burg /usr/sbin/update-grub
```

all this read in this forum and some blogs ):P

---


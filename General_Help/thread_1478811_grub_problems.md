---
title: "grub problems"
date: 2010-05-10
forum: General Help
---

### Post by harryliddic on 2010-05-10
My dual-boot in grub does not see winXP. It happened after I upgraded to 10.4. My guess is the grub up windows below 10.4 in priority which windows doesn't like. I am completely ignorant of how to adjust grub. I can't even get it to to come up as a program in the terminal. I need some kind soul to walk me through the steps of re-adjusting the grub so winXP is on top. if that is the problem.Also references to other threads would be appreciated.

---

### Post by dino99 on 2010-05-10
[http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

### Post by harryliddic on 2010-05-10
I ran your thread and through all the code at went by quickly I found the following
> Found Microsoft Windows XP Professional on /dev/sda1
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 00b48fd2b48fc91c
	drivemap -s (hd0) ${root}
	chainloader +1
}

does this mean anything to you?

---

### Post by Pritamsng on 2010-05-10
just boot in Ubuntu Live CD. 
mount the partation which contain /boot.
do "chroot <mounted partation>
then do grub-install <mounted partation>

---

### Post by harryliddic on 2010-05-10
The only Live Cd I have is from 9.10 will that work on 10.04?

---


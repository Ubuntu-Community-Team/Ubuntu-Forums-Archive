---
title: "A error occurred while Mounting /media/OS"
date: 2012-04-08
forum: General Help
---

### Post by twoAcestwo8s on 2012-04-08
Hi, Im somewhat new when it comes to using ubuntu had been running 10.10 before, Im currently running the 12.04 beta since I read they fixed the battery life kernel bug. Anyway when I started up my pc today i got this message "An error occurred while mounting /media/OS", press S to skip or M to manual Mount". I dont know what is wrong, I couldnt find anything about this when I googled it (though I found some similar "mounting error" threads but none that helped me). I dont know if this is an actual problem or if its because im running a beta build and its a bug. Either way any help would be much appreciated. Heres my fstab:


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
#Entry for /dev/sda4 :
UUID=2108113f-3f66-4b8b-aa3c-d0d10347195c	/	ext4	errors=remount-ro,user_xattr	0	1
#Entry for /dev/sda3 :
UUID=00B8457CB8457168	/media/OS	ntfs-3g	defaults,locale=en_US.UTF-8	0	0
#Entry for /dev/sda2 :
UUID=AA40A50D40A4E0F5	/media/RECOVERY	ntfs	defaults,nls=utf8,umask=0222	0	0

---

### Post by stevenwscott on 2012-04-08
I've seen that when a NTFS partition is marked dirty, like if Windows crashed or something.

---


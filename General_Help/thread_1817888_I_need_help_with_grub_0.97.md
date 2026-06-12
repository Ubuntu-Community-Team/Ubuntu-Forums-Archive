---
title: "I need help with grub 0.97"
date: 2011-08-03
forum: General Help
---

### Post by as009988 on 2011-08-03
Something got messed-up with grub. A reinstall is not A Option.  booting from livecd, chroot,install grub, fails.

What I need is how to tell the kernel that "/" is on /dev/md0 
software raid0   

here are my partions
 sda grub mbr
 sda1 /boot           (will mount on livecd)
 sda2 linuxraid md0   
 sda3 linuxraid md1 

 sdb1 swap
 sdb2 linuxraid md0
 sdb3 linuxraid md1

 md0 /                (will mount on livecd)
 md1 /home            (will mount on livecd)

after grub fails I  enter;
 root (hd0,0)
 kernel /vmlinuz-26.32-23-generic /=/dev/md0
 initrd /initrd-26.32-23-generic
 boot  

It loads a lot of stuff then a error.
"give up wating for root device"
drops to initramfs
There is a md0, and md1 in /dev/at this point.
 
 "/=/dev/md0"  is this right?

---

### Post by dandnsmith on 2011-08-04
I think, but couldn't be sure with the raid stuff, that
root=/dev/md0
would be the correct form to use, based on past non-raid experience.
HTH

---

### Post by as009988 on 2011-08-04
Thank you dandnsmith
root=/dev/md0 
was correct, It booted
:D:D:D
Now to find out what happened to grub.

Mark as solved.

---


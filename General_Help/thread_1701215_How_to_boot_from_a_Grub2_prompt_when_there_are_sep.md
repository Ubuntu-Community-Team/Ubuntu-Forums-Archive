---
title: "How to boot from a Grub2 prompt when there are separate /boot and / partitions"
date: 2011-03-06
forum: General Help
---

### Post by Roaring Silence on 2011-03-06
I was yesterday evening experimenting inserting a script into /boot/grub/grub.cfg. Well I broke grub.cfg and had to try to boot from a grub2 prompt.
I have separate /boot and / partitions on /dev/sda1 and /dev/sda2 respectively.
Working out the correct syntax for the boot to work was a little complicated, so I thought it would be useful to post the correct procedure here, in case anyone else has the same set up that I do (separate /boot and / partitions)
At the grub prompt code:

grub> set prefix=(hd0,1)/grub
grub> insmod linux
grub> set root=(hd0,2)
grub> linux (hd0,1)/vmlinuz-2.6.32-30-generic root=/dev/sda2 ro
grub> initrd (hd0,1)/initrd.img-2.6.32-30-generic
grub> boot

There were many kernel panics, not to mention panics of my own before I finally got it sorted out.

---

### Post by kiyop on 2011-03-06
The following line is not necessary, is it?
```
grub> set root=(hd0,2)
```

---

### Post by Roaring Silence on 2011-03-06
I am not certain, but I thought it was. It worked, anyway.
I removed the script from grub.cfg, now all is well.
I don't want to go to the trouble of disabling grub.cfg to check that.
If you have my set-up, feel free to try. Good luck.

---

### Post by kiyop on 2011-03-06
I think the line "set root=..." is not necessary if the file names of kernel and initramfs (and other necessary files) are written after preceding (hd*,@), which indicates the partition where the kernel and initramfs are.

I have confirmed that my thought is correct in grub2 command line.

I succeeded in booting ubuntu correctly without the line "set root=...".

---

### Post by Roaring Silence on 2011-03-06
Yes you are correct. I thought that it needed to be stated for the kernel to find /dev/sda1, but it seems not.
Anyway I hope that recording this saves someone with separate /boot and / partitions some time in future.

---


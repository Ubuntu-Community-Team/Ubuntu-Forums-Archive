---
title: "Wubi failed to boot my ubuntu after an update"
date: 2009-12-27
forum: General Help
---

### Post by wujj123456 on 2009-12-27
I installed 9.10 using wubi. After an update, I only saw the sh-grub prompt. 

Such fail occurs both on ubuntu 9.10 desktop 32/64-bit. This first install is always good, until I boot into ubuntu and update my system. It's about 160 packages updated, including a grub2 update. 

I have windows 7 64-bit installed. Hardware: E8400, 2*2G DDR1333 RAM, GTX 260+, gigabyte EP45T-UD3LR (rev1.0). Nothing special. Bios is the latest stable version F5, though there's an update on same model, which is for rev1.1, not rev1.0. 

I've dug a bit on the forum and found: 
[http://ubuntuforums.org/showthread.php?t=1320546](http://ubuntuforums.org/showthread.php?t=1320546)
It's an old thread and my problem is a bit different, though very similar. 

I don't have a live CD and I use ls in grub prompt to determine my ubuntu kernel version. 
For 64-bit, it's vmlinuz-2.6.31-16-generic-pae. BTW, what does this pae mean? 
For 32-bit, it's vmlinuz-2.6.31-14-generic, as it is in the thread mentioned above. 
System is in D: partition, which is (hd0,3)

So I did (32-bit example): 
sh:grub>insmod ntfs
sh:grub>set root=(hd0,3)
sh:grub>loopback loop0 /ubuntu/disks/root.disk
sh:grub>set root=(loop0)
sh:grub>linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro
sh:grub>initrd /boot/initrd.img-2.6.31-14-generic
sh:grub>boot

After I execute boot, it proceed to: 
...
[6.xxxxxx] io scheduler noop registered
[6.xxxxxx] io scheduler anticipatory registered
[6.xxxxxx] io scheduler deadline registered
[6.xxxxxx] io scheduler cfq registered (default)
then directly reboot. 

What should I do? Thanks.

---

### Post by Newt_Othis on 2009-12-28
Hi wujj123456

I have also had the same (or similar) problem running 64 bit 9.10 thru WUBI on Win 7 64 bit. Been running fine since october and then a batch of updates killed it.

Being a relative linux noobie - I am struggling to make sense of the sh:grub commands

I tried to enter the commands, but I think it is possible that I'm not entering the correct IDs for the system locations - I need to have a read and learn how Linux references the hard drive. (My WUBI Ubuntu folder is in the root of my C drive - which is the main SATA disk)

I'm going to have another go later.

BTW - pae is Physical Address Extension which is generally used by 32bit systems to actually operate as a 36bit system and address more RAM than the OS normally would - a 64bit system wouldn't need pae. I thought it was an Intel/Microsoft thing though.

Good luck with that - please post if you fix it.

Newt

---


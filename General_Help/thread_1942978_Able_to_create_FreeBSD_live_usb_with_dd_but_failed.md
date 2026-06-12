---
title: "Able to create FreeBSD live usb with dd but failed to do so for linux distros"
date: 2012-03-18
forum: General Help
---

### Post by accessgranted on 2012-03-18
Hello all and great board. I was previously trying to get a FreeBSD live usb running and couldn't. So I decided to format the disk with type a5 which is the FreeBSD type filesystem. Then I knew I had to mkfs but didn't see a .ufs for the Unix filesystem, so I went ahead and just did mkfs.ext3 /dev/sdx1. After that, I ran:

dd =if=/mnt/sdx/xxx.iso of=/dev/sdx1 bs=10240

Plugged it in a diff laptop and boom it worked perfectly. Couldnt believe it.

Now I am trying to make live usb just like that but with linux distros using the plain old ext3 filesystem for assigning type in fdisk. You would think it should work but I'm just dropped into a grub rescue prompt. I tried this with 2 linux distros, BT4 (i know it is old) and CentOS, the latest one.

When I create the CentOS with the same dd command issued above, I end up with a iso9660 filesystem that is ro. I tried to remount it in rw and it seemed to register in the shell but doesn't actually mount that way. I tried to grub-install the new device even though that sounds a bit strange, but I figured I would give it a shot, and that failed as well.

Why is the new usb filesystem an iso96600, mounting in ro and not booting into the distro when I did something simple and backwards for the FreeBSD usb and worked like a charm?

I am aware I can use Live USB creators but prefer to stick with the shell-based text-mode.
Thanks for any input.

---

### Post by accessgranted on 2012-03-19
I was able to figure it out. I omitted the partition number from the dd command. Instead of using of=/dev/sdb1, i tried it with just /dev/sdb. Works great. So nice and simple to make a live usb from the command line.  

1) format device in fdisk using ext3 filesystem and assign a for active  
2) mkfs.ext3 /dev/sdx1  
3) dd if=/path/to/isofile.iso of=/dev/sdx bs=10240 (doesnt seem to matter too much, i like to use 10240, 4096 works well, 8M is fine, etc  
4) umount  /dev/sdx1
5 enjoy

---


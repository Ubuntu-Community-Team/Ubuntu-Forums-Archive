---
title: "grub &amp; error 15"
date: 2009-12-25
forum: General Help
---

### Post by Th3Professor on 2009-12-25
I put a fresh OS install on and it wouldn't boot, it came up with error 15 during the grub load.

My partitions are as follows:

sda1 = /boot
sda2 = (windows)
sda5 = /

I have a couple "currently unused" partitions, though they are formatted with ext3... sda9 and sda10.

I loaded grub via livecd (I had to install grub while running livecd) and it said that my "stage1" is on (hd0,9). I want everything boot & grub related to be on /dev/sda1 (which is hd0,0 right?).

How do I put all grub & boot related apps/files into /dev/sda1 and set-up grub to boot from there instead of "(hd0,9)"?

thanks!

edit-
I took 2 approaches to try to reset grub (including installing it) so that hopefully it will now boot, I'm about to check it out, but it still has "(hd0,9)" and I'd like it to be (hd0,0) instead. Anyway here are the 2 approaches i used...

1st approach:

boot live cd
sudo grub
<didn't work at first, had to sudo apt-get install grub while running live cd>
sudo grub
find /boot/grub/stage1
<it brought up hd0,9 ...I have no idea why that partition>
root (hd0,9)
setup (hd0)
quit

2nd approach, I did this before even testing the 1st approach:

from the live cd
sudo mkdir /mnt/root
sudo mount -t ext3 /dev/sda5 /mnt/root
sudo mount -t ext3 /dev/sda1 /mnt/root/boot
sudo mount -t proc none /mnt/root/proc
sudo mount -o bind /dev /mnt/root/dev
sudo chroot /mnt/root /bin/bash
sudo grub
<didn't work, so I installed grub, I have no idea why I had to install it, I thought it was already there...>
sudo grub
find /boot/grub/stage1
<it brought up (hd0,9)>
root (hd0,9)
setup (hd0)
quit

...basically the same approach except I did it all from the actual new OS install the 2nd time around.

Anyway, I'm about to test booting into the OS but in the mean time, can someone help me with how to get *all* boot & grub related things running from "(hd0,0)" instead of "(hd0,9)"?

Thank you! :D

edit 2:

Okay, sda10 has a not-working attempt at an install of gentoo. lol I'm just going to format that partition. That will hopefully take care of the "(hd0,9)" thing. Then, well, I guess I can just put my install disc in again (it's an "alternate", actually it's ubuntu studio 9.10 dvd), and I'm going to see if I can skip the install process and go right to the grub section and do a fresh grub install. (???)

Will that do the trick?

---

### Post by pbrane on 2009-12-25
Have you seen this?
[http://linuxers.org/howto/how-fix-grub2-error-15-ubuntu]("http://linuxers.org/howto/how-fix-grub2-error-15-ubuntu")

---

### Post by Th3Professor on 2009-12-25
I haven't seen that. I tried using it just now and ended up with a problem with the /dev - /dev is now *missing*, only after I attempted taking care of another partition/disk, very weird - I'm going to have to do a fresh install again of the new OS. Fortunately it's kind of quick.

The confusing side of all of this is... I'm using LVM, and raid5 (mdadm). So far the mdadm is not mixed in with the current issue (the install auto-detected both raid & lvm) and my OS is not on the same hard drive as the multiple raid disks. So that's good.

The issue I'm running into now is I had an old sda10 partition for a Gentoo install and I also had a "/nomad" directory (via LVM/raid) that I created and was using as a mount point for what apparently was *another* gentoo install. <whoops!> It's kind of confusing. So right now I'm just going to disregard the raid/lvm disks (sdb, sdc, sdd) and focus only on the sda (OS hard drive). Hopefully this fresh install will fix things. :confused: ...*then* I can try that link out with the "how to fix grub". <shrug>

---


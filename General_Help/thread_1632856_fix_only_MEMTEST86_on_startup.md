---
title: "fix only MEMTEST86 on startup"
date: 2010-11-28
forum: General Help
---

### Post by Grahaman27 on 2010-11-28
I posted on a different thread about a certain error that I may be still having, but this time its different. It is now how it was before I skrewed my computers boot and partitions up even more. I have only one OS to boot, ubuntu 10.10.

When I start up my computer, It boots straight to memtest86. I did the hold shift trick to look at my boot menu and I only see memtest86 as an option to boot...

How do I fix the boot to my Ubuntu?

---

### Post by Grahaman27 on 2010-11-28
when I boot to a live cd and chroot in and install grub, then update, It does not even show my OS...

what is my problem? grub or my partition?

---

### Post by drs305 on 2010-11-28
The problem appears to be that you don't have a kernel installed in sda1. RESULTS.txt can not find a vmlinuz file or an initrd.img 

If this is the case it would also explain why you don't have any entries in your grub.cfg

From the LiveCD, you can mount /dev/sda1 and then inspect the boot folder to see if a kernel and initrd image exist:
```
sudo mount /dev/sda1 /mnt
nautilus /mnt/boot
```

If they don't exist, chroot into sda1 as you have done previously (Step 1 of from the G2-Chroot link in my signature line). Once you get to the root prompt, install the latest kernel and then update-grub. Inspect the /boot folder to make sure the kernel and initrd files exist before rebooting.

In the 'chroot' (you don't use 'sudo' in chroot):
```
apt-get update
apt-get install linux-image
update-grub

```

Exit chroot and see if that solves things.

---

### Post by Grahaman27 on 2010-11-28
the only kernel that shows up on an update-grub in chroot is memtest-

Found GRUB 2: /boot/grub/core.img
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

is the directions to install latest kernels in one of your links? im currently in chroot at the moment.

---

### Post by drs305 on 2010-11-28
> **Grahaman27 said:**
> is the directions to install latest kernels in one of your links? im currently in chroot at the moment.

If you are in 'chroot' and have the root prompt, all you need to do is run the commands I listed in my previous post.

```

apt-get update
apt-get install linux-image
update-grub

```

---

### Post by drs305 on 2010-11-28
> **Grahaman27 said:**
> is the directions to install latest kernels in one of your links? im currently in chroot at the moment.

If you are in 'chroot' and have the root prompt, just run the commands I listed in my previous post.

```

apt-get update
apt-get install linux-image
update-grub

```

---

### Post by Grahaman27 on 2010-11-28
Ok, I just misunderstood. I did those Commands and now I get "error 11: unrecognized device string" perhaps I did something wrong? It showed vmlinuz/image something when I updated grub. I press enter after the error and have a menu that is much different, options being-

chainload into grub2 (goes back to error)
and
ubuntu 10.10, memtest86+ (just loads memtest)

and do I need grup-pc? because there was an error about that when Chrooting

---

### Post by drs305 on 2010-11-28
It sounds like you still have a mix of Grub legacy and Grub 2. 

I would run the purge/reinstall instructions (from the G2-Chroot link in my signature line) again, but run the purge commands one at a time, and include grub. If you get any error messages, exit chroot, umount everything and start again;

```
apt-get purge grub
apt-get purge grub-pc
apt-get purge grub-common
apt-get install grub-pc
```
The fourth command will install both grub-common and grub-pc and then should run update-grub as part of the installation process. Make sure to select only "sda" when it gets to the partitioning section, and watch that the udpate-grub command finds the linux image.

---

### Post by Grahaman27 on 2010-11-28
Ok I just realized, when looking in my boot folder that the initrd.img and vmlinuz are not in there, just a grub folder. but I did find those two files on "/" the root folder, Is that what I want?

---

### Post by drs305 on 2010-11-28
> **Grahaman27 said:**
> Ok I just realized, when looking in my boot folder that the initrd.img and vmlinuz are not in there, just a grub folder. but I did find those two files on "/" the root folder, Is that what I want?

Normally there are initrd.img and vmlinuz entries in /. These are actually links to the kernel and initrd images in /boot, which would have names like *vmlinuz-2.6.35.22-generic* and *initrd.img-2.6.35-22-generic*. Of course, your version numbers may be different, and may or may not end with *generic*.

---

### Post by Grahaman27 on 2010-11-28
The last purging and reinstalling worked! My good ubuntu finally booted up!! thank you so much! It did have some sort of error when booting about disk drive not working, maybe that's my live CD/usb but as far as I can tell everything is working great.

any final steps to make this boot stick?

---

### Post by drs305 on 2010-11-28
> **Grahaman27 said:**
> The last purging and reinstalling worked! My good ubuntu finally booted up!! thank you so much! It did have some sort of error when booting about disk drive not working, maybe that's my live CD/usb but as far as I can tell everything is working great.

any final steps to make this boot stick?

Not really. As long as update-grub was run in chroot it should remain in a working condition. I don't think there is anything else you need to do except tweaking the /etc/default/grub settings to your preferences (timeout, etc). You might make a backup of /boot/grub/grub.cfg and put it somewhere so you have a reference if something should break later.

Don't know what the disk drive error is unless there is a reference to something in /etc/fstab (perhaps listings for your removed partitions) that needs cleaning up.

But I'd just start enjoying a working Ubuntu.

:-)

---

### Post by Grahaman27 on 2010-11-28
yup, that was definitely the first thing I did. now... Is it possible to use chroot to install packages to your system? because I uninstalled network-manager and other packages leading me to a internetless device (all my stupidity).

---

### Post by Grahaman27 on 2010-11-28
nevermind, I got It, chrooting is so useful. working wonderfully.

---


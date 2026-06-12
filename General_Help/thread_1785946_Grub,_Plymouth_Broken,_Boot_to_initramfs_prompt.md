---
title: "Grub, Plymouth Broken, Boot to initramfs prompt"
date: 2011-06-19
forum: General Help
---

### Post by dragonboss on 2011-06-19
OK, so after following [this]("http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/") guide using 1024x768 resolution as test, my pc is not able to boot to ubuntu(x64), and halts at an initramfs prompt. How can this be fixed? Posting this from my laptop (1st in my signature)

---

### Post by prodigy_ on 2011-06-19
Boot from LiveCD and use Boot Info Script: [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

It will create a file named RESULTS.TXT. Post the contents of the file here.

---

### Post by dragonboss on 2011-06-19
That is not going to be possible because I have no physical live cd, and I deleted the isos I had on the laptop

---

### Post by prodigy_ on 2011-06-19
Doesn't have to be a CD but (depending on what exactly went wrong) you might really need something you can boot from.

---

### Post by dragonboss on 2011-06-19
Currently downloading the iso again. It will take a while its at 65% now and estimates 12min remaining.

---

### Post by wildmanne39 on 2011-06-19
> **dragonboss said:**
> OK, so after following [this]("http://http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/") guide using 1024x768 resolution as test, my pc is not able to boot to ubuntu(x64), and halts at an initramfs prompt. How can this be fixed? Posting this from my laptop (1st in my signature)Hi, you should be able to by pass that with this link, then you can reset your resolution after you boot, if this does not work let us know.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

---

### Post by dragonboss on 2011-06-19
The iso finally downloaded and here is the results.txt

---

### Post by drs305 on 2011-06-19
One thing I noticed in your RESULTS.txt is that /etc/fstab isn't shown in your Ubuntu partition. In my RESULTS.txt the /etc/fstab file is always found and it's location reported in the Ubuntu partition. At boot you could go to the Grub prompt (press "c") and type:
```
ls (hd0,6)/etc/fstab
``` 
It should return: fstab

Another thing to try would be to simplify the 'linux' line to see if it's your options that are causing the boot to fail. Highlight the menuentry and press 'e' to edit it. Use the cursor and DEL keys to shorten it to the following and see if it boots:
> linux	/vmlinuz-2.6.38-8-generic root=/dev/sda1 ro  nomodeset 
CTRL-x to boot.

Note: I also edited your first post to correct the linked address. It started with "http://http://" ...

---

### Post by dragonboss on 2011-06-19
Ok I'm going to reboot and try this, as I'm currently using the live cd(iso).

---

### Post by dragonboss on 2011-06-19
ls (hd0,6)/etc/fstab returns error: file not found

---

### Post by dragonboss on 2011-06-19
linux	/vmlinuz-2.6.38-8-generic root=/dev/sda1 ro nomodeset boots to initramfs prompt. The last error message states No init found. Try passing init= bootarg.

---

### Post by drs305 on 2011-06-19
> **dragonboss said:**
> linux	/vmlinuz-2.6.38-8-generic root=/dev/**[COLOR="Red"]sda1[/COLOR]** ro nomodeset boots to initramfs prompt. The last error message states No init found. Try passing init= bootarg.

I didn't notice this the first time around since I was concerned about the lack of an fstab file and the numerous options, but the highlighted area should point to your Ubuntu partition ([COLOR="DarkRed"]**sda6**[/COLOR]). That is probably the cause of the initramfs problem, although the missing fstab file still puzzles me.

---

### Post by dragonboss on 2011-06-19
ok, rebooting and trying again. My boot is on its own partition. Is this the cause of the problem with the missing fstab?

---

### Post by dragonboss on 2011-06-19
Still boots to initramfs.I'm also noticing these errors:

[  16.081197] uvesafb: mode switch failed (eax=0x34f, err=0). Trying again with default timings.
[  16.555469] (same error as above)

---

### Post by drs305 on 2011-06-19
The separate /boot partition may explain why fstab isn't displayed. I'd not noticed that behavior of the boot info script but it's possible that is the reason.

So you have a btrfs /boot folder on sda1. Try manually booting this from the grub prompt:

```
set root=(hd0,1)
set prefix=(hd0,1)/grub
linux /vmlinuz-2.6.38-8-generic root=/dev/sda6 ro nomodeset
initrd /initrd.img-2.6.38-8-generic
boot
```

If it boots, run "sudo update-grub".

Added: If it doesn't work, can you boot the recovery mode? You may have to rebuild the initrd image, which could be done from the command line or by chrooting from a LiveCD.

---

### Post by prodigy_ on 2011-06-19
[edit: removed]

---

### Post by dragonboss on 2011-06-19
linux /vmlinuz-2.6.38-8-generic root=/dev/sda6 ro nomodeset
initrd /initrd.img-2.6.38-8-generic

This returns error: file not found.

---

### Post by drs305 on 2011-06-19
You say you have a separate /boot but the boot files all appear to be on sda6.

If you think you have a separate /boot folder, where do you think it is?

From what RESULTS.txt is reporting, the boot commands should be:

> set root=(hd0,6)
set prefix=(hd0,6)/boot/grub
linux /vmlinuz root=/dev/sda6 ro nomodeset
initrd /initrd.img
boot

Which if you still get an initramfs failure probably means you have to rebuild the image.

Also, to make sure your BIOS can see the Grub files, at the prompt do you get a return with these commands:
> ls (hd0,6)/boot
ls (hd0,6)/boot/grub

---

### Post by dragonboss on 2011-06-19
The boot partition is supposed to be a 977MB ext4 partition on /dev/sda6, under a 2.0GB extended partition, according to the Disk Utility on the live CD.

---

### Post by dragonboss on 2011-06-19
That does not show the files, but ls (hd0,6) shows the files:
lost+found/ grub/ system.map-2.6.38-8-generic (e.t.c.) initrd.img-2.6.38-8-generic

---

### Post by drs305 on 2011-06-19
Ok, got it. sda6 is your /boot folder and is your install on sda1 (btrfs)? I don't think I've seen this setup but it should work as long as BIOS can see your /boot files.

From your last post:
> 
That does not show the files, but ls (hd0,6) shows the files:
lost+found/ grub/ system.map-2.6.38-8-generic (e.t.c.) initrd.img-2.6.38-8-generic 

Is there also a "vmlinuz-2.6.38-8-generic" 

If so, and sda1 is your Ubuntu installation (other than /boot):

> set root=(hd0,6)
set prefix=(hd0,6)/grub
linux /vmlinuz-2.6.38-8-generic root=/dev/sda1 ro nomodeset
initrd /initrd.img-2.6.38-8-generic
boot

---

### Post by dragonboss on 2011-06-19
> **drs305 said:**
> You say you have a separate /boot but the boot files all appear to be on sda6.

If you think you have a separate /boot folder, where do you think it is?

From what RESULTS.txt is reporting, the boot commands should be:



Which if you still get an initramfs failure probably means you have to rebuild the image.

Also, to make sure your BIOS can see the Grub files, at the prompt do you get a return with these commands:

ls (hd0,6)/boot error: file not found.
ls (hd0,6)/boot/grub error: file not found.

---

### Post by dragonboss on 2011-06-19
Yes there is a vmlinuz on there.

---

### Post by drs305 on 2011-06-19
> **dragonboss said:**
> ls (hd0,6)/boot error: file not found.
ls (hd0,6)/boot/grub error: file not found.

We're stepping on each other a bit. Those results make sense now that I know where you /boot and installation are. See my previous post. I expect you to still get the initramfs error, which means you will need to either boot to the recovery mode, if possible, or to the LiveCD, where you would chroot into your real installation and then use the update-initramfs command to rebuild the image. I can't vouch for the kernel options you are using, so I'd try to simplify them as much as possible just to get it booting again.

---

### Post by dragonboss on 2011-06-19
set root=(hd0,6)
set prefix=(hd0,6)/grub
linux /vmlinuz-2.6.38-8-generic root=/dev/sda1 ro nomodeset
initrd /initrd.img-2.6.38-8-generic
boot

This worked, but still boots to initramfs prompt.

---

### Post by prodigy_ on 2011-06-19
> **dragonboss said:**
> This worked, but still boots to initramfs prompt.
One note re. your results.txt. You used btrfs for sda1. While being mostly stable at this point, btrfs is still under development and lacks fsck utility. More info here: [https://help.ubuntu.com/community/btrfs#Stability](https://help.ubuntu.com/community/btrfs#Stability)

Everything else looks alright except missing fstab as **drs305** already mentioned. This may be the cause of the busybox promt because fstab defines filesystems which should be mounted at boot time including root filesystem.

Boot again from LiveCD and mount your /dev/sda1 somewhere. E.g.
```
mount /dev/sda1 /mnt
```
Then check if **etc** directory exists (a little sanity check)```
ls -l /mnt/etc
```
and if it does edit fstab
```
nano /mnt/etc/fstab
```

You need to add at least these lines if fstab is indeed empty:
```

proc		/proc	proc	nodev,noexec,nosuid		0	0
/dev/sda1	/		ext4	errors=remount-ro	0	1
/dev/sda5	none	swap	sw				0	0

```

---

### Post by drs305 on 2011-06-19
> **prodigy_ said:**
> Everything else looks alright except missing fstab as **drs305** already mentioned. This may be the cause of the busybox promt because fstab defines filesystems which should be mounted at boot time including root filesystem.

That's a good point. We never resolved whether it's a RESULTS.txt issue or if /etc/fstab is in fact missing. See if you can find it with:
```
ls (hd0,1)/etc/fstab
```

---

### Post by dragonboss on 2011-06-19
/etc does not exist on /dev/sda6,  which I find strange myself.

---

### Post by dragonboss on 2011-06-19
> **drs305 said:**
> That's a good point. We never resolved whether it's a RESULTS.txt issue or if /etc/fstab is in fact missing. See if you can find it with:
```
ls (hd0,1)/etc/fstab
```

Result:

error:file not found.

P.S. What is going on with the etc? Where the heck is it? I don't understand.

---

### Post by prodigy_ on 2011-06-19
> **dragonboss said:**
> /etc does not exist on /dev/sda6,  which I find strange myself.
It shouldn't be on sda6 in your case because sda6 is boot partition. Look for it on sda1. If **etc** exists on sda1 and **etc/fstab** defines all the necessary mount points then you need to chroot into your installation and carefully revert the changes you made to your configs. Don't forget to rebuild initramfs:
```
initramfs -u
```
and update grub.cfg:
```
update-grub
```

---

### Post by dragonboss on 2011-06-19
OK OK I've found it! Its in (hd0,1)/@/etc/fstab!
Now what do I do?

---

### Post by dragonboss on 2011-06-19
Am I supposed to chroot into my installation? How is this done?

---

### Post by dragonboss on 2011-06-19
I'm having problems with the chroot into my system. Need some help.

---

### Post by dragonboss on 2011-06-19
Followed the chroot part step by step:

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008448d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       24323   195366912   83  Linux
/dev/sda2           24323       24566     1954817    5  Extended
/dev/sda5           24323       24447      999424   82  Linux swap / Solaris
/dev/sda6           24447       24566      954368   83  Linux

Disk /dev/sdb: 8180 MB, 8180989952 bytes
252 heads, 62 sectors/track, 1022 cylinders
Units = cylinders of 15624 * 512 = 7999488 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006218a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1022     7983833    c  W95 FAT32 (LBA)
ubuntu@ubuntu:~$ sudo mount /dev/sda1
mount: can't find /dev/sda1 in /etc/fstab or /etc/mtab
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt/@
mount: mount point /mnt/@ does not exist
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
ubuntu@ubuntu:~$ sudo mount /dev/sda6 /mnt/@/boot
ubuntu@ubuntu:~$ for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt$i; done
mount: mount point /mnt/dev does not exist
mount: mount point /mnt/dev/pts does not exist
mount: mount point /mnt/proc does not exist
mount: mount point /mnt/sys does not exist
ubuntu@ubuntu:~$ for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/@$i; done
ubuntu@ubuntu:~$ sudo chroot /mnt
chroot: failed to run command `/bin/bash': No such file or directory
ubuntu@ubuntu:~$ sudo chroot /mnt/@
root@ubuntu:/# update-grub
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
```

---

### Post by dragonboss on 2011-06-19
I can cd into dev but it can't update grub?

---

### Post by dragonboss on 2011-06-19
Seems I'm alone on this one...

---

### Post by drs305 on 2011-06-19
Just logged back on to the forums and I see you have made some progress.

First, if your problem is just a result of a misplaced fstab, you may not need to chroot at all.  The easiest thing it try is just to mount your /dev/sda1 and then copy or move the fstab file back into the *etc* folder. This assumes the /etc folder exists (and not just in /@) - otherwise you want to move /@/etc to /etc within the mountpoint.

From a LiveCD:
```
sudo mount /dev/sda1 /mnt
gksu nautilus /mnt
```
From here, either copy or move fstab back to /mnt/etc or move the entire *etc* folder from /mnt/@ to /mnt. You want the entire *etc* folder and contents under / (or on the LiveCD, under /mnt/ ).

You don't need to update-grub or chroot if this is the only problem. If you have questions, I'll be logged on for a while.

---

### Post by dragonboss on 2011-06-19
It seems you have posted too late, as I got impatient and have already started moving my stuff off the drive in preparation for a fresh install.
Any advice on how to properly create a separate boot partition this time?
And also why is the drive in that structure, @, @home?

---

### Post by drs305 on 2011-06-19
Most users don't need a separate /boot partition unless their BIOS has a limitation, and even then you can just ensure the / partition is under that limitation. If you are going to use a format that is incompatible with Grub 2 you would also need a separate /boot partition. 

I'd make /boot at least 500 MB since the trend seems to be for Grub to include more and more things in the /boot/grub folder. Long ago, 50 MB was plenty, today that isn't enough.  I'd probably also make it a primary partition and I'd make all the partitions manually with Gparted and then specify them during the installation. I never quite trust the installation partitioning, although if you have backed up/moved all your data that might not be a big deal.

I tend to keep my installations separate from my data but that's personal choice. Another option is to make a separate /home partition, and keep your data in it. The advantage is mainly to preserve most of your user configuration files when you upgrade to a newer release.

As far as the @ problem in your previous installation, that was definitely a big part of the problem; how you ended up with @ folders I have no idea...

---

### Post by dragonboss on 2011-06-19
Ok, say for example you have a 250GB hdd, how would you partition it? In terms of home boot e.t.c.

---

### Post by drs305 on 2011-06-19
> **dragonboss said:**
> Ok, say for example you have a 250GB hdd, how would you partition it? In terms of home boot e.t.c.

It's all pretty subjective, but with a /boot and /home partition to hold your configurations and all your data:
Primary Partition:
/boot  500MB

Extended Partition:
Logical (sda5)
/ - 15-20 GB (Could be as small as 10GB)
Logical (sda6)
/home - the rest of the drive if you don't want a separate data partition
Logical (sda7)
/swap (at the end of the drive) - 2GB, depending on your RAM.

For my own, I just have:
50 GB Primary (data/future use/future OS on primary)
Extended:
/ - 20GB per OS
The rest are various data partitions.
2GB swap at the end of the drive.

---

### Post by dragonboss on 2011-06-19
Thanks for all the help!
P.S. I happened to have about 50GB reserved for Windows and never got around to using it.

---


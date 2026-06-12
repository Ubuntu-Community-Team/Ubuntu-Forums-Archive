---
title: "Unable to boot due to swap partition change"
date: 2006-04-12
forum: General Help
---

### Post by m0bilitee on 2006-04-12
Hi folks -

I had to move my swap partition from hda4 to another partition due to some repartitioning stuff.  I modified the /etc/fstab, built the swap manually with mkswap, etc.

When ubuntu boots the kernel, it hangs on the graphical boot at "loading modules", so I tried recovery mode. It hangs with the following:

attempting manual resume
attempt to access beyond end of device
hda4: rw=16, want=8, limi=2
Kernel panic - not syncing: I/O error reading memory image

Of course there's an I/O error, hda4 doesn't exist anymore.  

I've tried booting editing the grub entry for the recovery mode and adding "noresume" but it INSISTS on trying to boot this way--how can I get around this and get in?

thanks!

m0b

---

### Post by taurus on 2006-04-12
Boot the LiveCD, mount your Ubuntu somewhere and paste the output of the following two commands from a terminal here...
```

more /mnt/ubuntu/etc/fstab <-- assuming that you mount it to /mnt/ubuntu!
sudo fdisk -l /dev/hda

```

---

### Post by m0bilitee on 2006-04-19
fstab, typed across into another machine (forgive my typos please!)


[FONT="Courier New"]proc          /proc            proc    defaults  0 0
/dev/hda3  /                  ext3    defaults,errors=remount-ro 0 1
/dev/hda1  /media/hda1   vfat     defaults 0 0
/dev/hda2  /media/hda2   ntfs     umask=0222 0 0
/dev/hda6  none             swap    sw  0 0
/dev/hdc   /media/cdrom0 udf,iso9660 user,noauto 0 0[/FONT]

fdisk:

[FONT="Courier New"]/dev/hda1            1          7           56196    de   Dell Utility
/dev/hda2    *      8      2618     20972857+    7   HPFS/NTFS
/dev/hda3       2619      5050     19535040    83   Linux
/dev/hda4       5051      7296     18040994      f   W95 Ext'd (LBA)
/dev/hda5       5051      6835     14337981      7   HPFS/NTFS
/dev/hda6       6836      6959       995998+     82  Linux swap[/FONT]


What I can't figure out is if I add "noresume" on the Grub kernel options, it still tries to resume. Where in configuration does it think that the old hda4 partition is the resume/swap partition?  Or do I have this wrong?

---

### Post by m0bilitee on 2006-04-20
Okay, I'm finally in. I got this fixed by adding 

resume=/dev/hda6

on my Grub options for the kernel I boot to.  I added it to menu.lst in /boot/grub as well, so it's "permanent", but if I take it off the system keeps going back to /dev/hda4.  So, I'm thinking the next time I upgrade kernels it will "revert back."  

So, is this part of initrd?

---

### Post by jomtois on 2006-05-17
I think I have the same problem and I am going to try the resume=/dev/hxxx like you suggested and see if that gets me anywhere.

I have also seen in another post that you might be able to edit

/etc/mkinitrd/mkinitrd.conf to set that permanently...haven't tried that yet either, since I can' boot yet.

From what I gather, this has to do with the suspend/hibernate/resume function.  I never use those, and do not intend to.  I think when you suspend, it dumps the current state to the swap partition.  As far as I'm concenred it might as well dump it to /dev/null.  Actually, would setting it in /etc/mkinitrd/mkinitrd.con as resume=/dev/null even work or would that be a bad idea???

---

### Post by jomtois on 2006-05-18
[QUOTE=jomtois]
I have also seen in another post that you might be able to edit

/etc/mkinitrd/mkinitrd.conf to set that permanently...haven't tried that yet either, since I can' boot yet.[/QUOTE]

Okay, so that didn't work...the file didn't exist anyway.  I think there was a /etc/mkinitramfs directory that I went into that had a conf.d subdirectory with one entry called resume.  I set that to the proper /dev/hdxxx and was confident that would apply the change.  It did not.

This is what I did that worked, although I do not know how much was actually necessary:

Went to synaptic and completely removed all kernels. (Ignored all warnings about how I could hose my system -- I know, it is a little risky)
Completely removed Grub
Completely removed initramfs-tools and init-scripts
Reinstalled them all

Checked my /boot/grub/menu.lst to make sure everything was kosher.

Rebooted, all went as expected with swap partition working correctly.

As an afterthought, maybe doing dpkg-reconfigure on the above packages would have accomplished the same thing?  I am still learning, so I don't know exactly how everything works yet.

Don't know if this helps or not, but it worked for me.

Jon

---

### Post by Firetech on 2006-06-16
[QUOTE=jomtois]Went to synaptic and completely removed all kernels. (Ignored all warnings about how I could hose my system -- I know, it is a little risky)
Completely removed Grub
Completely removed initramfs-tools and init-scripts
[/QUOTE]

Ok, that was a bit overkill, but it gave me a direction into the needed steps. (See below)

[QUOTE=jomtois]As an afterthought, maybe doing dpkg-reconfigure on the above packages would have accomplished the same thing?[/QUOTE]

You're actually right. :)

_Here comes 'The more safe way to do it (without removing your kernels)':_
**0.** If you haven't booted yet, use Grub's handy features to edit the boot command (press 'e', and read the instructions on the bottom. You should add "resume=/dev/hdxx" in the end of the line that begins with "kernel".
**1.** Edit "/etc/mkinitramfs/conf.d/resume" (needs sudo) to contain the right device address.
**2.** Run "sudo dpkg-reconfigure initramfs-tools" and wait a moment (it took about a minute for me, with one kernel installed).
**3.** Reboot, rejoice and start breathing again. (If it doesn't work, check the spelling everywhere, most of the stuff is case sensitive.)

---

### Post by marklid on 2006-08-29
I had exactly the same problem as the original poster - and Firetech's solution worked a treat !
Cheers - save me a reinstall !! :D

---

### Post by koto on 2006-09-20
I also had exactly the same problem (Ubuntu 6.06 - system froze at "mounting root filesystems" after manually repartitioning drive and moving swap partition).

Firetech solution worked great! You could add it somewhere to the wiki I suppose.

---

### Post by richardjennings on 2007-03-01
im back into ubuntu at last :):):)  THANKYOU!!!

---

### Post by ethanay on 2008-06-04
Just to update: for Hardy 8.04 the location to update is:
/etc/initramfs-tools/conf.d/resume

run ```
update-initramfs -u
``` after changing the above file

and of course, update your fstab partitions accordingly :)

then all should work again.  /dev/null wouldn't work, I don't think, because that is where you are telling Ubuntu to look for the resume data :)

---


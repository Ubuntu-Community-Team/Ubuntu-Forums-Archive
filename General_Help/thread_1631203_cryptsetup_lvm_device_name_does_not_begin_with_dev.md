---
title: "cryptsetup: lvm device name does not begin with /dev/mapper/"
date: 2010-11-26
forum: General Help
---

### Post by potiphera on 2010-11-26
I'm running 64-bit Ubuntu Studio 10.04 with the preempt kernel and full disk encryption.  I installed some updates and restarted, and now Ubuntu won't start, and I see a cryptsetup message saying that the lvm device name (long name starting with /dev/disk/by-uuid/) does not begin with /dev/mapper/.  After a little while it drops to a shell.  How do I fix this?  I might be able to use the generic kernel, but I can't seem to get to the GRUB menu (Esc doesn't work), so if anyone can tell me how to even get into GRUB, I would appreciate it.  Thanks!

---

### Post by potiphera on 2010-11-26
Never mind, I solved this.

I didn't realize that the proper way to enter GRUB is by holding down the Shift key.  Once I did that, I saw that I had an old generic kernel (2.6.32-24-generic) set as the default.  Newer kernels worked fine, so I just used StartUp-Manager to select one of those as default instead.

---

### Post by potiphera on 2011-01-04
I installed the most recent kernel update, and the problem reoccurred.  The problem is that now I can't even get into GRUB at all: after I press Shift, it tells me it's starting GRUB, and then I get some error messages that only display for a split second, and then the error saying that the lvm device name does not begin with /dev/mapper/.  How can I fix this?  I had to use a live CD of 10.04 to post this, and it won't let me mount my encrypted filesystem, so editing any of my regular Ubuntu installation's user or system files from the live CD is impossible.

---

### Post by potiphera on 2011-01-04
I figured out how to mount my encrypted volume from a live CD from [this thread]("http://ubuntuforums.org/showthread.php?t=940904").  Still need to learn how to fix GRUB, though.

---

### Post by potiphera on 2011-01-05
OK, I realized that the error I was getting is "udevadm trigger is not permitted while udev is unconfigured."  So I found [this thread]("http://ubuntuforums.org/showthread.php?t=1567147").  I barely understand most of it, but I tried following Audi200Q's advice from the first page, except using the chroot instructions from [here]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202") after mounting my encrypted volume.  Everything worked perfectly up until the sudo update-initramfs -u -k 2.6.32-27-preempt and sudo update-initramfs -u -k 2.6.32-27-generic commands, which gave me some errors saying "cryptsetup: WARNING: invalid line in /etc/crypttab -".  I still can't get my system to boot.  What should I be doing?

---

### Post by potiphera on 2011-01-06
(bump) Still unable to use my system.

---

### Post by potiphera on 2011-01-07
I decided to [downgrade to GRUB legacy]("https://help.ubuntu.com/community/Grub2#Uninstalling%20GRUB%202").  Now I can get into the GRUB menu, and I have the correct filesystem path set, but I get an error saying "No init found.  Try passing init= bootarg."  What does this mean?  I ran fsck on the boot and encrypted partitions, but I still get the error.

---

### Post by potiphera on 2011-01-08
I ran update-initramfs to generate new initrd.img files, but that didn't solve the problem either.  However, each time I did it, I got two errors saying "cryptsetup: WARNING: invalid line in /etc/crypttab -".  Not sure why -- /etc/crypttab looks fine to me.  I still get the "no init found" error when I try to boot.

---

### Post by potiphera on 2011-01-09
(bump) I haven't been able to use my system for almost a week; any ideas?  I also tried Super Grub Disk to no avail.

---

### Post by potiphera on 2011-01-10
OK, I was going to try using the GRUB rescue utilities on the alternate install CD, but first I decided to upgrade GRUB back to the new version.  And then the GRUB rescue and GRUB reinstallation stuff kept giving me fatal errors.  So I think at this point my plan is to reinstall everything.  I worry, however, that this problem could reoccur, since I'm still not sure what caused it.  So if anyone has any idea, feel free to tell me so I can avoid having to reinstall again.

---

### Post by bababooey on 2011-03-24
I have the same problem too. Used a livecd and had no problem getting into my encrypted root/home. Ran dpkg-reconfigure grub-pc and linux-image-2.6.35-28-generic and 2.6.35-27-generic, update-initramfs, updated my fstab and crypttab using UUID's only, but I cant figure this one out. I must have used the livecd to go in my encrypted system like 10x with a big fail after each reboot. Grub is installed into my drive's mbr, grub.cfg looks okay. Did a google search and found a bunch of bug reports but not much help with the evms error. I never spent so much time getting no where fixing my box after i got started with dmcrypt. Seeing no one helped you here, I guess i'll scrap my setup, reinstall, and use truecrypt instead. The reason why I used dmcrypt in the 1st place because I like how it ask you for a password to gain access and then keyfiles can be used to mount the rest of the encrypted partitions.

---


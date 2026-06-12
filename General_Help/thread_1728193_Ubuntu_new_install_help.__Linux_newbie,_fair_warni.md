---
title: "Ubuntu new install help.  Linux newbie, fair warning!"
date: 2011-04-13
forum: General Help
---

### Post by Mister Earl on 2011-04-13
Just did a full install of the latest version of Ubuntu.  I've got a  high-end alienware m17x laptop with dual SSD drives in a raid array.   Ubuntu installed fine, but when I reboot, I get to a grub rescue prompt  and it never gets to desktop.  I'm booting from the liveCD while I try  to figure out how to fix it.

Mount gives me this:

ubuntu@ubuntu:~$ mount
aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
/dev/sr1 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/mapper/nvidia_aiachche1 on /media/9ce176d0-f6e5-4bd7-ab8b-aeda57a9228e type ext4 (rw,nosuid,nodev,uhelper=udisks)

sudo grub install gives me this: (logged in as root)

root@ubuntu:~# sudo grub-install /dev/mapper/nvidia_aiachche1
/usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).

All the guides tell me to sudo fdisk -l, which gives me this:

root@ubuntu:~# sudo fdisk -l
Unable to seek on /dev/sda

---

### Post by Mister Earl on 2011-04-13
If anyone could lend a hand, I'd be grateful.  I've spent six hours trying to fix this with no success.

---

### Post by odysseusjak on 2011-04-13
I wish I could point you in a direction...

Have you checked the documentation for anything with RAID?

---

### Post by Mister Earl on 2011-04-13
Not yet, no.  I *think* it's seeing my hard drives.  Under "places" I'm seeing the combined drive, anyway.  With what appears to me to be what was installed earlier.

---

### Post by sanderd17 on 2011-04-13
I asume it's RAID 1 (since you only have 2 drives). If it's RAID 0 (that not RAID in fact) you should not call it RAID.

Did you try to do the installation procedure over? And check in gparted on the live disk what SSD's he sees.

---

### Post by Mister Earl on 2011-04-13
> **sanderd17 said:**
> I asume it's RAID 1 (since you only have 2 drives). If it's RAID 0 (that not RAID in fact) you should not call it RAID.

Did you try to do the installation procedure over? And check in gparted on the live disk what SSD's he sees.

Yes, I've done a complete install via live disk multiple times.  I believe this is the fourth.  I've formatted all partitions each time.  Not sure how to do gparted, can you walk me through it?

Total linux / ubuntu newbie here.

---

### Post by Mister Earl on 2011-04-13
Ok, gparted didn't want to run for whatever reason.  So I ran the install link from the live CD desktop, and went along until the advanced partition options.  It's showing me two partitions right now:

/dev/mapper/nvidia_aiachche1, type ext4, size 491GB
/dev/mapper/nvidia_aiachche5, type swap, 20.8GB

---

### Post by ronparent on 2011-04-13
> root@ubuntu:~# sudo grub-install /dev/mapper/nvidia_aiachche1
This is the wrong location for a raid boot loader.

The command ought to be:
> sudo grub-install /dev/mapper/nvidia_aiachche
I am guessing at the actual name - it is the first name in /dev/mapper and  is the name of the array without a partition number. 

If you are booting from the raid the boot loader must be in the MBR for the array as a whole.

---

### Post by Mister Earl on 2011-04-13
Gave me this error:
/usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).

Gotta call it quits for now... time to run to work.  I'll try again in about nine hours.

---

### Post by ronparent on 2011-04-13
All that message is saying is that the default location for installing grub is not being found. 

To begin at the beginning. Assuming you have a valid install to the raid (/dev/mapper/nvidia_aiachche1, type ext4, size 491GB) you need to use the two step method for reinstalling grub 2 (ref. [https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB 2).

Boot on a live cd and write the following commands to a terminal:

> sudo mount /dev/mapper/nvidia_aiachche /mnt

sudo grub-install --root-directory=/mnt/ /dev/mapper/nvidia_aiachche

That should fix you up properly. Post if you need more help.

---

### Post by Mister Earl on 2011-04-14
Still having trouble, I'm afraid.  Results:

ubuntu@ubuntu:~$ sudo mount /dev/mapper/nvidia_aiachche /mnt
mount: /dev/mapper/nvidia_aiachche already mounted or /mnt busy

ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/ /dev/mapper/nvidia_aiachche 
/usr/sbin/grub-probe: error: cannot find a device for /mnt//boot/grub (is /dev mounted?).

I saw that double slash, so I tried this:

ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/mapper/nvidia_aiachche 
/usr/sbin/grub-probe: error: cannot find a device for /mnt/boot/grub (is /dev mounted?).


No luck.

---

### Post by Mister Earl on 2011-04-14
Wonderful!  Ignore the above.  I managed to un-raid things, repartitioned and reformatted everything.  Installed Ubuntu, and now it boots fine!  Last remaining problem:  It boots to a black screen.  I know to use nomodeset, but it boots so bloody quick I can't manage to do it before I hear the ubuntu jingle.  So, how can I effect this change via live CD?

---

### Post by Mister Earl on 2011-04-14
Ok, and nevermind to the above, there.  Working.  I can now boot from hard disk and get to desktop.  Now to add graphics drivers...

---

### Post by ronparent on 2011-04-14
I know you don't need this anymore but it was my bad! The commands I should have given you were:
> sudo mount /dev/mapper/nvidia_aiachche1 /mnt
to mount the partition, then
> sudo grub-install --root-directory=/mnt/ /dev/mapper/nvidia_aiachche 
to install grub to your system in /dev/mapper/nvidia_aiachche1 and the boot loader at /dev/mapper/nvidia_aiachche. 

And yes the extra / is needed in the second command. I'm sorry for messing you up.

---


---
title: "Wubi/GRUB crash.  Can't mount disk.  Help!"
date: 2011-03-10
forum: General Help
---

### Post by ZZalgern0n on 2011-03-10
Hi there!

Last night, I tried to restart my comp, and all the kernel listings for Ubuntu were gone.  GRUB was giving me errors.  I can boot into Windows fine but can't get into Ubuntu. 

I'm currently in a LiveBoot of Linux and trying commands seen here:

[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

sudo mkdir /media/win  
sudo mount /dev/sda**2** /media/win 
sudo mount -o loop /media/win/ubuntu/disks/root.disk /mnt 
sudo cp /mnt/boot/grub/grub.cfg /mnt/boot/grub/grub.cfg.copy 
sudo chmod +w /mnt/boot/grub/grub.cfg 
gksu gedit /mnt/boot/grub/grub.cfg

But I'm having errors at trying to mount the disk.  

My partition is on sda2.  When I type the:

sudo mount /dev/sda2 /media/win

I get:

Mount is denied because the NTFS volume is already exclusively opened.
The volume may be already mounted, or another software may use it which
could be identified for example by the help of the 'fuser' command.

Help!  Thanks!

---

### Post by ZZalgern0n on 2011-03-10
Okay.  I tried

sudo umount /dev/sda2

Then:

sudo mount /dev/sda2 /media/win

It appears to be mounted there now.  However:

ubuntu@ubuntu:~$ sudo mount -o loop /media/win/ubuntu/disks/root.disk /mnt
/media/win/ubuntu/disks/root.disk: No such file or directory

I can see in the file structure under /media/win/ubuntu/

That there is no 'disks' folder.  I appear to be missing a key ingredient?  Where can I find or copy from?

---

### Post by ZZalgern0n on 2011-03-10
Okay.  Myriad searching through these forums popped up the fix:

Windows DiscCheck moved the files to a hidden folder on the c:\

c:\FOUND.000

Put them all into the c:\ubuntu\disks

All is well.

QUESTION -- Since WUBI seems quite overloaded by Windows memory appetite and this appears to be an annoying bug, what is the best and most stable way to introduce an Ubuntu partition on the HD?  I don't want to damage my Windows in case of backup.

Thanks!

---

### Post by Mark Phelps on 2011-03-10
> **ZZalgern0n said:**
> ... c:\FOUND.000 
This is a sign that CHKDSK found some corrupted files.  That is the default it uses with those files.  If you're writing to your Windows filesystem while inside Ubuntu, it can cause such filesystem corruption.

>  what is the best and most stable way to introduce an Ubuntu partition on the HD?  I don't want to damage my Windows in case of backup. Thanks!

If you want to experiment with dual-boot, and you're running Win7, BEFORE you do anything else, use the Win7 Backup feature to create and burn a Win7 Repair CD.

Then, open up a terminal in Ubuntu and enter "sudo fdisk -lu" (that's a lowercase L, not a one). This will list off the partitions on your drive.  IF you already have four partitions, installing Ubuntu to its own is going to be major work.

---

### Post by Rubi1200 on 2011-03-10
As Mark Phelps mentioned, Windows chkdsk utility probably moved the files there.

Be careful with excessive fragmentation on Windows if you have a Wubi install; best to defragment on a regular basis.

You can also copy the root.disk to a safe location such as an external drive or USB stick. If something like this happens again, just copy it back to its original location.

Post the output of the command asked for so we can advise you on either migrating the Wubi install to its own partition or going for a fresh install from the LiveCD.

Finally, make sure to lock the grub-* packages as outlined in the main post here:
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

---


---
title: "What should I do after clean first 200mb data in /dev/sda by mistake?"
date: 2012-08-03
forum: General Help
---

### Post by ytj on 2012-08-03
Hello, all:

Just right now, I intent to exec ``dd if=/dev/zero of=/dev/sdb`` to test the
speed of my new usb disk. However, I made a mistake, ran ``dd if=/dev/zero
of=/dev/sda``. When I realized what I have done, I typed Ctrl-C, it reported
that it written 200MB in /dev/sda. Now my partition table is missing, maybe MBR.
I get panic and dare not reboot my computer. 
I remenber before I destroyed the partition table, the partitions are::


/dev/sda
/dev/sda1 ext2 100MB (mount on /boot)
/dev/sda2 ntfs 20GB (for Windows, have no important data)
/dev/sda3 ntfs 100GB (for windows, have no important data)
/dev/sda5 ext4 400GB (mount on /)
/dev/sda6 swap 5GB


I think the root directory have not got damage.
My system looks OK right now, Just no files in /boot.
How can I recover the partition table and /boot?

---

### Post by BkkBonanza on 2012-08-03
I can't guarantee this but it seems you lucked out in not wiping your root partition (/dev/sda5).

First thing I'd do is,

sudo umount /boot

so that your /boot directory is back on / (where it is safe for now). Then comment any /boot mount line in /etc/fstab.

Next, try to fix the MBR. Assuming you're using Grub (the default), and that / is mounted still,

sudo grub-install /dev/sda
sudo update-grub

That should put the MBR back at start of /dev/sda and install grub related stuff in /boot again. If you get errors here you may have to fix /boot up first.

If you happen to have backups of your /boot directory then I'd restore from that. If not then I guess you'll need to restore the kernel images and whatnot manually. You could try using apt-get install for _your_ current kernel and see if that re-writes the needed stuff. You may need to use --reinstall or some other option to try and force it. If that doesn't go easily you may need to locate and restore the files manually. Once you have /boot set up then I think you can reboot and see if it takes. If not then you'll need to revisit grub-install/update grub to make sure your MBR and /boot are sync'd and working. Don't reboot unless you have the kernel images in /boot as otherwise you'll be stuck fixing this from a LiveCD.

If you succeed with all that then I'd use GParted (system menu) to check sda1 and sda2 and recreate them (set filesystem and format). You'll lose everything on those two partitions but you can re-use them. Once you have sda1 rebuilt you can copy /boot over to there and fix up your mount in fstab again.

Gee. What else? I probably forgot something here.

---

### Post by oldfred on 2012-08-03
You may be able to recover partition table if not rebooted.

If not rebooted, use fdisk to manually recreate table posts by srs5694 post34 (page 4):
[http://ubuntuforums.org/showthread.php?t=1668247](http://ubuntuforums.org/showthread.php?t=1668247)

---

### Post by lukeiamyourfather on 2012-08-03
Backup everything that you don't want to lose before doing anything else. If you haven't backed up everything already. ;)

---


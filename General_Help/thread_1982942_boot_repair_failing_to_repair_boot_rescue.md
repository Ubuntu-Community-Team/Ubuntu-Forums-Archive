---
title: "boot repair failing to repair boot rescue"
date: 2012-05-19
forum: General Help
---

### Post by pfene on 2012-05-19
I used boot repair to try to repair my computer from the boot rescue menu, how ever it tesll me the system is repaired but when I boot it still goes to the boot menu.
The Ubuntu pastebin URL is [http://paste.ubuntu.com/996037/](http://paste.ubuntu.com/996037/)
I am not jacked-up with Linux I will appriciate a detailed help.
Thanks in advance

---

### Post by Mark Phelps on 2012-05-19
Unfortunately, I ran into some serious problems getting a 12.04 install to work, and I was NEVER able to get BOOT-REPAIR to fix it.  It just loaded and kept running -- and never finished.  I had to end up completely replacing the hard drive.

You would get more help if you told us, in detail, why you're running boot-repair.

---

### Post by oldfred on 2012-05-19
Boot-Repair is only seeing your Windows install, so that is the fix it does.

Your sda6 was not mounted, so it may have some issue the e2fsck can fix.

#From liveCD so everything is unmounted,swap off if necessary, change example shown with sda6 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems.
sudo e2fsck -C0 -p -f -v /dev/sda6
#if errors:
sudo e2fsck -f -y -v /dev/sda6

Then boot-repair may see your sda6 Linux partition and let you reinstall grub2's boot loader using that partition.

---

### Post by pfene on 2012-05-23
sudo e2fsck -f -y -v /dev/sda6

worked and my Ubuntu drive is now mounted.
I run boot repair and now Grub is working as normal

Thanks

---


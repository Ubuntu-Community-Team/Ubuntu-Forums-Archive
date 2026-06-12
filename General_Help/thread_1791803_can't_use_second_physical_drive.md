---
title: "can't use second physical drive"
date: 2011-06-27
forum: General Help
---

### Post by halibaitor on 2011-06-27
I installed a 30 gig hard drive for extra storage space.  It is currently using the ext2 file system.  When looking at it in gparted, there is a key icon next to the drive.

I would like to use this drive for storage with programs running in WINE, but can't even see the drive from there.  From the normal OS, I can see and mount the drive, but can't use it for anything.

I am going to go out on a  limb and guess that the key icon means it is locked somehow.  How do I unlock/use this drive?  Is there a command to use in the terminal, or within the Disk Utility that will do it?

Any suggestions are welcome.

---

### Post by dandnsmith on 2011-06-27
Usually the lock symbol means the filesystem is mounted, and therefor not amenable to changes.
In a terminal, if you do 'sudo mount' that should show you what is mounted.
As a 2nd HDD it may be showing as sdb, but that isn't guaranteed.
If mounted, you can use 'sudo umount' - I suggest you consult the man pages for more detail, if you need it.

---

### Post by halibaitor on 2011-06-27
It does show up as sdb1, which is what i would have expected.

I don't understand how the key icon means it is mounted, because that showed up when I formatted it in gparted, before i had a chance to mount it.  (sda1 does not show that icon in gparted)

I just want to be able to use the drive for something, and am going crazy trying to figure this out.  If I format it as a FAT32, then I can at least use it with my OS, but it is still invisible to the programs running in WINE.  I don't think FAT32 is a good system to use with Ubuntu anyhow...

What is "man pages"?  I'm kind of a noob.  Can you give me a link?

---

### Post by oldfred on 2011-06-27
Man pages are help or definitions of commands used in the terminal or other settings.

From a terminal type:
man wine 
or
man fstab
man mount

You just have to know it it q to exit from the man page back to the terminal.

I just looked in my wine as I only use it for Picasa. It actually sees all my NTFS & FAT partitions which I mount with fstab. Even the USB flash drive I have plugged in.

If it is a permanent hard drive you will want to mount with an entry in fstab so on reboots you do not have to manually remount it.

Understanding fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
Above link was this post before:
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)
HOWTO: Mount NTFS partitions with specific ownership/permissions 
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

---


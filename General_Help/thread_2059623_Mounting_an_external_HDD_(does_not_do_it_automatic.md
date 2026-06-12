---
title: "Mounting an external HDD (does not do it automatically)"
date: 2012-09-18
forum: General Help
---

### Post by cheerPuncH on 2012-09-18
Hi,

I'm working on Ubuntu Server. 10.04.2 LTS. I plugin in a Touro Desk Hitachi 4TB/To. I cannot find anywhere on the box or in the manual what type of file system it is. However, it does state on the box that it is compatible with Windows7, WindowsXP, Windows Vista and with MacOS 10.5 or newer. Is there a way to determine what file system it is through the terminal? (yes, I've searched online) I've also looked at [http://ubuntuforums.org/showthread.php?t=353487]("http://ubuntuforums.org/showthread.php?t=353487") this thread which is very simliar to my issue. I would mount the external but I don't know what file system it is. I've taken some snips of information about my computer and attached them to the thread. Any help getting this to mount would be greatly appreciated.

Thanks!

Here is the external HDD web page [http://www.hgst.com/external-drives/desktop/touro-desk]("http://www.hgst.com/external-drives/desktop/touro-desk")

Also this webpage [http://www.cyberciti.biz/faq/linux-how-to-determine-find-out-file-system-type/]("http://www.cyberciti.biz/faq/linux-how-to-determine-find-out-file-system-type/") states that Linux "supports Ext2,. Ext3, NFS, FA16, FAT32, NTFS,Sysfs, Procfs etc.". 
But the man pages states [http://manpages.ubuntu.com/manpages/hardy/man8/mount.8.html]("http://manpages.ubuntu.com/manpages/hardy/man8/mount.8.html")
"       -t vfstype
              The argument following the -t  is  used  to  indicate  the  file
              system   type.   The  file  system  types  which  are  currently
              supported include: adfs, affs,  autofs,  cifs,  coda,  coherent,
              cramfs,  debugfs,  devpts,  efs,  ext, ext2, ext3, hfs, hfsplus,
              hpfs, iso9660, jfs, minix, msdos, ncpfs, nfs, nfs4, ntfs,  proc,
              qnx4,  ramfs,  reiserfs,  romfs,  smbfs,  sysv, tmpfs, udf, ufs,
              umsdos, usbfs, vfat, xenix, xfs,  xiafs.   Note  that  coherent,
              sysv  and  xenix are equivalent and that xenix and coherent will
              be removed at some point in the future &#8212; use sysv instead. Since
              kernel  version  2.1.21  the  types  ext  and xiafs do not exist
              anymore. Earlier, usbfs was known as usbdevfs.  Note,  the  real
              list of all supported filesystems depends on your kernel."
I'm starting to believe that the **external HD is a FAT32**.

ionadmin@ionT01:/$ sudo **mount -t vfat /dev/sdb1 /mnt/ExternalArchive**
mount: wrong fs type, bad option, bad superblock on /dev/sdb,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Would I have to re-format the external HDD?

---

### Post by cheerPuncH on 2012-09-18
I figured it out. The file system is NTFS as seen in the **sudo fdisk -l** command.
The following command worked.
```
sudo mount -t ntfs /dev/sdb1 /mnt/ExternalArchive 
```

Is there a way to delete this thread?

---

### Post by thnewguy on 2012-09-18
You may be able to mount the external drive without specifying a specific file system type. Sometimes the system can guess. For example, this might do the trick:

sudo mkdir -p /media/disk
sudo mount /dev/sdb1 /media/disk

You say "re-format", but I wonder if the drive is formated at all? Assuming no one has put any data on the drive yet, it is safe to partition and format the drive with whatever file system you like.

To check to see if any partitions exist on the disk and if they have been formated, try running cfdisk on the drive and see what comes up.

sudo apt-get install cfdisk
sudo cfdisk /dev/sdb1

---


---
title: "can't unmount or format USB drive"
date: 2012-10-05
forum: General Help
---

### Post by yer916 on 2012-10-05
so I used startup disk creator which screwed up my USB drive and now I can't unmount it or format it.

here's what I get when I type blkid:

```
/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D9-0619" TYPE="vfat" 
/dev/sda2: UUID="06C8DF6BC8DF578F" TYPE="ntfs" 
/dev/sda5: UUID="ba6884af-3d02-4f50-886f-ff0cc3022cd3" TYPE="ext4" 
/dev/sda6: UUID="1e301d39-df10-4e17-a07f-c2659345e4de" TYPE="swap" 
/dev/sdb1: LABEL="ure>^M^J</Pac" UUID="E716-2B13" TYPE="vfat" 
dave@dave-Studio-1737:~$ mount
/dev/sda5 on / type ext4 (rw,errors=remount-ro,user_xattr,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/dave/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=dave)
/dev/sdc1 on /media/ure>
<_Pac_ type vfat (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sda2 on /media/06C8DF6BC8DF578F type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb1 on /media/ure>
<_Pac__ type vfat (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)

```

it seems as though the drive is mounted with a name that has 2 lines... which makes everything I tried impossible.

trying to unmount with Disk Utility gives me this error: "Error unmounting: umount exited with exit code 1: umount: /media/ure>: not found"

please help :[

---

### Post by yer916 on 2012-10-05
Ok, so I was finally able to format the thumb drive, but now there are FIVE permanent "ure></Pac" drives appearing as mounted drives, even when the thumbdrive isnt plugged in.

they are named
ure>
<_Pac

ure>
<_Pac_

ure>
<_Pac__

etc... 
blah, please help

---

### Post by yer916 on 2012-10-05
screenshot:

---

### Post by yer916 on 2012-10-05
nevermind, fixed it... just used "gksudo "gnome-open %u"" and sent the folders to trash that way as root.

---


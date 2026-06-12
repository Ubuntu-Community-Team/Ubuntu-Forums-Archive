---
title: "partitioning my HD"
date: 2012-05-05
forum: General Help
---

### Post by MrGrado on 2012-05-05
Can I partition my hard drive without wiping what's already on it? If yes, how?

I have a 2TB drive and I am running ubuntu 11.10. 

I want a partition for windows vista, also is there any advantage to having a 3rd partition to store files that I may wish to access from either OS.

---

### Post by jonnyboysmithy on 2012-05-05
Boot a livesystem and use the application "gparted" Fantastic tool for partitioning.
You HAVE to be running a livesystem. You cannot partition the disk while its being used by the OS on the disk.
If you need help with the live system go ahead and ask.

Might be handy to have a partition with all your data that you can access from vista and ubuntu. I know one of my friends does that.

---

### Post by oldfred on 2012-05-05
If you want to install Windows it depends on your install. 

Windows will only install to a primary NTFS partition with the boot flag in MBR(msdos) partitioning.

Windows will only install to gpt partitioning if you boot with UEFI.

If your drive is 2TB and you used a Ubuntu default install, you probably have gpt?

Post this:

sudo parted /dev/sda unit s print

---

### Post by MrGrado on 2012-05-05
> Model: ATA Maxtor 6L200M0 (scsi)
Disk /dev/sda: 398294975s
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start       End         Size        Type     File system  Flags
 1      63s         286712054s  286711992s  primary  ntfs         boot
 2      286712055s  398283479s  111571425s  primary  ntfs

thank you for your assistance.

---

### Post by oldfred on 2012-05-05
No Ubuntu shown, is this Wubi in another Windows install?

Then you are into booting two Windows?

---

### Post by MrGrado on 2012-05-05
Ubuntu is the only OS on my hard drive.

---

### Post by jerome1232 on 2012-05-05
> **MrGrado said:**
> Ubuntu is the only OS on my hard drive.

Not possible with just an NTFS drive, sounds like your using Wubi.

What is the output of this command?

```
mount
```

---

### Post by MrGrado on 2012-05-05
> /dev/sdb2 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/mrgrado/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=mrgrado)
/dev/sdc1 on /media/PENDRIVE type vfat (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)


.

---

### Post by jerome1232 on 2012-05-05
Ah, your linux partitions are on a second disk :D /dev/sdb

I'm not sure where oldfred was going with this so I'll leave the rest to him.

---

### Post by MrGrado on 2012-05-05
I think I can plug a USB hard drive in and boot up in kubuntu, if that will provide a real simple solution.

---

### Post by oldfred on 2012-05-05
Not sure what sdb is, but if you want Windows I would install to the sda drive. then the Windows boot loader is on sda, Ubuntu can have its boot loader on sdb and you set sdb to boot in BIOS. If issues with sdb you can directly boot Windows in sda.

What is in the sda drive or how full are partitions? You should be able to shrink the partitions and create another NTFS primary partition with the boot flag. Windows will then install to that partition. Since you already have two NTFS partitions why do you want another.

If you only have data in the sda partitions you can use gparted to shrink them. If Windows 7 you should only use Windows 7 to shrink partition but not to create partitions as it may try to convert entire drive  to dynamic which does not work with Linux.

---


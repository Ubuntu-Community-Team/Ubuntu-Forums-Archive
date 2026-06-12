---
title: "Can't seem to change my windows partition mount to READ-ONLY"
date: 2012-01-01
forum: General Help
---

### Post by Geoff16W on 2012-01-01
I am dual booting, running windows 7 and Ubuntu 11.10. When the system starts up my Windows file system is mounted and provides me with read-write access. 

I recently experienced some file corruption while transferring back and forth between operating systems, and I decided it would be best to make this file system read-only. 

But when I go to properties->permissions of the mounted file system and change the permissions to read-only, it just changes back to its original setting. What gives?

I also thought I could go into /etc/fstab and change one of the options to "ro", but can anyone tell me why I don't see this file system listed there even when it is mounted? I was under the impression that if a drive is mounted then it would be listed in this file. But only the linux partition and swap are listed.

Thanks for your help

---

### Post by fdrake on 2012-01-01
> **Geoff16W said:**
> I also thought I could go into /etc/fstab and change one of the options to "ro", but can anyone tell me why I don't see this file system listed there even when it is mounted? I
that's the /etc/mtab you are talking about!
before you assign the partition to fstab first get some info about the partition for us:
```

sudo fdisk -l
sudo blkid

```

---

### Post by Geoff16W on 2012-01-02
Ok here's the read out from the /etc/mtab


/dev/sda5 / ext4 rw,errors=remount-ro,user_xattr 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
udev /dev devtmpfs rw,mode=0755 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
tmpfs /run tmpfs rw,noexec,nosuid,size=10%,mode=0755 0 0
none /run/lock tmpfs rw,noexec,nosuid,nodev,size=5242880 0 0
none /run/shm tmpfs rw,nosuid,nodev 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/jeffrey/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=jeffrey 0 0
/dev/sda3 /media/0A928ADD928ACD1F fuseblk rw,nosuid,nodev,allow_other,blksize=4096,default_permissions 0 0

Below is the read-out out from sudo fdisk -l


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xfd591a55

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       80324       40131   de  Dell Utility
/dev/sda2           81920    30801919    15360000    7  HPFS/NTFS/exFAT
/dev/sda3   *    30801920   271619759   120408920    7  HPFS/NTFS/exFAT
/dev/sda4       271620094   312580095    20480001    5  Extended
/dev/sda5       271620096   308533247    18456576   83  Linux
/dev/sda6       308535296   312580095     2022400   82  Linux swap / Solaris

As you can see my windows file system is /dev/sda3 and in the /etc/mtab it is mounted to /media/0A928ADD928ACD1F

I'd like to change the permissions so that it boots to READ-ONLY. I'm a bit of a newbie, so if you can give me explicit direction about how to modify /etc/mtab I would be grateful.

Here's the blkid read out if that helps.

jeffrey@jeff-ubuntu:~$ sudo blkid
/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="3030-3030" TYPE="vfat" 
/dev/sda2: LABEL="RECOVERY" UUID="CA30B19930B18D47" TYPE="ntfs" 
/dev/sda3: UUID="0A928ADD928ACD1F" TYPE="ntfs" 
/dev/sda5: UUID="bc44d7b5-252f-4d2a-94db-e3f458f3d91b" TYPE="ext4" 
/dev/sda6: UUID="135e4340-bc0c-4050-91ce-ce5327d54810" TYPE="swap" 

Thanks

---

### Post by audiomick on 2012-01-02
> **Geoff16W said:**
> 
But when I go to properties->permissions of the mounted file system and change the permissions to read-only, it just changes back to its original setting. What gives?

The windows partition will be an NTFS partition. This format does not support and therefore can't be assigned Linux permssions. I am afraid I don't know off hand of a way to achieve what you want.

If the partition is mounting automatically,  I would have expected it in fstab too, but I am completely out of my depth there.

---

### Post by Mark Phelps on 2012-01-02
If sda3 is your Windows OS partition, then you definitely do NOT want to automount it read/write.  Doing so is asking for trouble -- along the lines of filesystem corruption and failure to boot.

You could try editing the MTAB file and changing "rw" to "ro" on the line for the /media mount.  But, I don't know if that will "stick".

A better way might be to remove that line from MTAB and add a mount line to fstab, specifying "ro" for the Windows partition.

---

### Post by fdrake on 2012-01-02
you have 2 options:
A)install first some ntfs drivers and then edit the fstab with gedit and copy paste this line:
```

sudo apt-get install ntfs-3g ntfs-config
sudo mkdir /media/win
sudo gedit /etc/fstab

```

> 
UUID=0A928ADD928ACD1F    /media/win   vfuse   ro,auto,user,exec  0 0

save , and reboot to see if it works.
note: pay attention at the spaces!

B)another way is to use the option in ntfs-config. MAke sure you use either one not both!
```
sudo ntfs-config
```

---

### Post by Geoff16W on 2012-01-02
@fdrake, the solution of changing "rw" to "ro" in the mtab file, suggested by Mark Phelps above, seems the easiest. Is there a reason I should do what you suggest rather than what Marks suggest.

(I really appreciate your help with this)
jw

---

### Post by fdrake on 2012-01-02
/etc/mtab (mount table)lists the current mounted file-systems so it will change at a boot time. Fstab(file system table) is a configuration file read at boot time by the system, and tells the system how to and where to mount the file-systems.

---

### Post by oldfred on 2012-01-02
I do not know how to change the temporary mount's permissions. But you can make a permanent mount and make it read only or just a manual mount to test. Unmount your existing automount first.

sudo mkdir /media/windows
sudo ntfs-3g -o ro /dev/sda3 /media/windows


umount above if editing fstab also.
sudo umount /dev/sda3


Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)
HOWTO: Mount NTFS partitions with specific ownership/permissions - WorMzy
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

You do not want defaults as that is rw:
Since Hardy (or Intrepid), Ubuntu adds the relatime option by default.
relatime = relatime + defaults = relatime, rw, suid, dev, exec, auto, nouser and async

Options:
[http://linux.die.net/man/8/mount.ntfs-3g](http://linux.die.net/man/8/mount.ntfs-3g)

```
sudo cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab

```UUID is better but this will work:

```
# Entry for /dev/sda3 :"
/dev/sda3         /media/windows   ntfs-3g      ro            0  0

```# make sure you have no typos before rebooting
```
sudo mount -a
```If it has errors it will tell you or else it just returns to command line.

Edit, everyone else beat me to it.

You may be able to do this, but would have to do it on every reboot:
sudo mount /media/0A928ADD928ACD1F -o remount,ro,noatime

---

### Post by fdrake on 2012-01-02
+1 oldfred;

also reading oldfred's post I noticed i made a mistake in the file type in the fstab entry ; instead of "vfuse" it should be "ntfs-3g" which is part of fuse ;)

---

### Post by Geoff16W on 2012-01-02
Thanks everybody for your help.
Everything seemed to work fine. And I also learned a lot. Below is the new mtab file directly after boot-up.

jeffrey@jeff-ubuntu:~$ cat /etc/mtab
/dev/sda5 / ext4 rw,errors=remount-ro,user_xattr,commit=0 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
udev /dev devtmpfs rw,mode=0755 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
tmpfs /run tmpfs rw,noexec,nosuid,size=10%,mode=0755 0 0
none /run/lock tmpfs rw,noexec,nosuid,nodev,size=5242880 0 0
none /run/shm tmpfs rw,nosuid,nodev 0 0
/dev/sda3 /media/windows fuseblk ro,nosuid,nodev,allow_other,blksize=4096 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/jeffrey/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=jeffrey 0 0

Thanks

---

### Post by oldfred on 2012-01-02
Glad it worked.:)

If everything is fine, change thread to solved, so others searching forum may find solutions.

---


---
title: "Broke my live usb mounting of NTFS hard drive"
date: 2011-11-03
forum: General Help
---

### Post by Shaggin Shea on 2011-11-03
I use live usb ubuntu 11.04 and was attempting to edit fstab to mount my ntfs sda1 drive on boot up. This is the guide I used [http://ubuntuguide.org/wiki/Ubuntu:O..._privileges.29]("http://ubuntuguide.org/wiki/Ubuntu:Oneiric#Mounting_NTFS_Partitions_.28with_read.2Fwrite_privileges.29")

So here is my 

sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
240 heads, 63 sectors/track, 64601 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       62670   473785168+   7  HPFS/NTFS
/dev/sda2           62671       64601    14598360    7  HPFS/NTFS

Disk /dev/sdb: 8019 MB, 8019509248 bytes
20 heads, 16 sectors/track, 48947 cylinders
Units = cylinders of 320 * 512 = 163840 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008b1a3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       48948     7831512    c  W95 FAT32 (LBA)

I then did this 
sudo nano /etc/fstab

and added this line under the fstab
/dev/sda1 /media/WindowsNTFS ntfs-3g quiet,defaults,rw 0 0

Restarted the computer

So now it does not appear my drive mounts on boot up and instead when I try to open my drive through the file manager I get 

Unable to mount location
Error mounting: mount exited with exit code 16: Mount is denied because the NTFS volume is already exclusively opened.
The volume may be already mounted, or another software may use it which
could be identified for example by the help of the 'fuser' command.
When I check fstab the edit I made is no longer there
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0

I did fuser -m /dev/sda1 and this is what is returned

ubuntu@ubuntu:~$ sudo fuser -m /dev/sda1
Cannot stat file /proc/4212/fd/21: Stale NFS file handle
Cannot stat file /proc/4212/fd/22: Stale NFS file handle

ls -al /dev/sda1
brw-rw---- 1 root disk 8, 1 2011-10-29 09:52 /dev/sda1

ubuntu@ubuntu:~$ ls -l /media
total 8
drwx------ 2 root root 4096 2011-10-22 22:23 casper-rw
lrwxrwxrwx 1 root root    6 2011-08-17 12:48 cdrom -> /cdrom
drwxr-xr-x 2 root root 4096 2011-10-22 22:13 WindowsNTFS
ubuntu@ubuntu:~$ mount WindowsNTFS
mount: can't find WindowsNTFS in /etc/fstab or /etc/mtab
ubuntu@ubuntu:~$ ls -l /media/WindowsNTFS
total 0

---

### Post by dcstar on 2011-11-04
> **Shaggin Shea said:**
> I use live usb ubuntu 11.04 and was attempting to edit fstab to mount my ntfs sda1 drive on boot up. This is the guide I used [http://ubuntuguide.org/wiki/Ubuntu:O..._privileges.29]("http://ubuntuguide.org/wiki/Ubuntu:Oneiric#Mounting_NTFS_Partitions_.28with_read.2Fwrite_privileges.29")
..........

[LIST=1]
[*]Do not **eve**r follow any instructions that tell you to use /media for any mounting. **/media is a system folder for the exclusive use of the system** for mounting drives - not users. If you want to mount anything, then use /mnt or another mount point that you create in your system.
[*]Only a USB with Persistence will save any changes to any file that will be there after a reboot.
[/LIST]

---

### Post by Shaggin Shea on 2011-11-04
I was following the Ubuntu Guide! I would think that was a trusted source but now I am wary.

I did do this first if it means anything
sudo mkdir /media/WindowsNTFS

So the way I see it I wasn't trying to mount into the media folder. Rather a subfolder. Shouldn't that make a difference?

I am using persistence for my usb drive.

Does that help?

---

### Post by dcstar on 2011-11-04
> **Shaggin Shea said:**
> I was following the Ubuntu Guide! I would think that was a trusted source but now I am wary.

I did do this first if it means anything
sudo mkdir /media/WindowsNTFS

So the way I see it I wasn't trying to mount into the media folder. Rather a subfolder. Shouldn't that make a difference?


Be told, do **not** use /media.

---

### Post by Shaggin Shea on 2011-11-04
Ok I have been considered told but that doesn't fix my problem.

Can you help me fix this or should I just go to reinstall backup?

Please give me advice that as a novice which direction should I take.

Keep trying to fix the problem (I want to do this)?
Start new pendrive (probably easiest but I learn less).

---

### Post by Shaggin Shea on 2011-11-05
Bump

---

### Post by Shaggin Shea on 2011-11-07
bump

---

### Post by coffeecat on 2011-11-07
Hi. I completely disagree with the earlier comment about using /media for mounting partitions, so long as you use a sub-folder in /media, which you are doing. The standard mountpoint folders /mnt and /media are there for you to use - they work slightly differently. Just because automouting uses a sub-folder in /media doesn't mean that you can't use it as well.

The mounting error when you try to mount through the file manager is probably because the partition is mounted already through /etc/fstab. So that we can look at this afresh, boot up with the live USB and post the output of these terminal commands:

```
cat /etc/fstab
sudo blkid
mount

```

And you might as well post the output of fdisk again, just to make sure nothing has changed:

```
sudo fdisk -lu
```

fdisk -lu, not -l, please, if you are running 11.04.

Please post the output between [noparse]```
 and 
```[/noparse] tags for clarity.

I suspect the problem may be your ntfs mount options which are not optimal, but let's see that output before making a judgement.

**EDIT**: a thought for you to mull over. /dev/sda1 looks to be your Windows C: partition. Personally, I never set up my systems to mount Windows C: partitions on bootup. It's all too easy to accidentally damage Windows system files in a permanently mounted partition. Why not simply remove your /etc/fstab line and then your live session should be able to automount the Windows partition on as as-needed basis from the file manager. Much safer in my view.

---

### Post by Shaggin Shea on 2011-11-07
```
ubuntu@ubuntu:~$ cat /etc/fstab
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
```


```
ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/loop1: LABEL="casper-rw" UUID="bfacc137-0dea-774f-b760-0ed7683f2f67" TYPE="ext2" 
/dev/sda1: LABEL="HP" UUID="CE469F4C469F33E5" TYPE="ntfs" 
/dev/sda2: LABEL="FACTORY_IMAGE" UUID="949CA48C9CA46A86" TYPE="ntfs" 
/dev/sdb1: LABEL="PENDRIVE" UUID="16F1-3121" TYPE="vfat"
```

```
ubuntu@ubuntu:~$ mount
rootfs on / type rootfs (rw)
none on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
none on /proc type proc (rw,nosuid,nodev,noexec,relatime)
none on /dev type devtmpfs (rw,relatime,size=1665032k,nr_inodes=210546,mode=755)
none on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
/dev/sdb1 on /cdrom type vfat (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
/dev/loop1 on /cow type ext2 (rw,noatime,errors=continue)
aufs on / type aufs (rw,noatime,si=9d555618)
none on /sys/kernel/debug type debugfs (rw,relatime)
none on /sys/kernel/security type securityfs (rw,relatime)
none on /dev/shm type tmpfs (rw,nosuid,nodev,relatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev,relatime)
none on /var/run type tmpfs (rw,nosuid,relatime,mode=755)
none on /var/lock type tmpfs (rw,nosuid,nodev,noexec,relatime)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,nosuid,nodev,noexec,relatime)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,relatime,user_id=999,group_id=999)
/dev/sr0 on /media/New type iso9660 (ro,nosuid,nodev,relatime,uid=999,gid=999,iocharset=utf8,mode=0400,dmode=0500)
/dev/sdd1 on /media/A892-486C type vfat (rw,nosuid,nodev,relatime,uid=999,gid=999,fmask=0022,dmask=0077,codepage=cp437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro)
```

```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 500.1 GB, 500107862016 bytes
240 heads, 63 sectors/track, 64601 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   947570399   473785168+   7  HPFS/NTFS
/dev/sda2       947570400   976767119    14598360    7  HPFS/NTFS

Disk /dev/sdb: 8019 MB, 8019509248 bytes
20 heads, 16 sectors/track, 48947 cylinders, total 15663104 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008b1a3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          80    15663103     7831512    c  W95 FAT32 (LBA)
```

---

### Post by coffeecat on 2011-11-07
Three things.

1 - You didn't use code tags as I asked. Your terminal output is near unreadable. Have a look at this:

[http://ubuntuforums.org/showthread.php?t=1006656](http://ubuntuforums.org/showthread.php?t=1006656)

Put simply, you need to see this when you type the message:

[noparse]```
Your
terminal
output
```[/noparse]

Which will appear like this in your post:

```
Your
terminal
output
```

2 - Your sda1 /etc/fstab line that you mentioned in your OP is not there. Are you 100% sure you created persistence when you created the USB?

3 - I was adding an edit to my previous post while you were posting. You may not have seen this. I've got to log off for an hour or so now, so have a think about what I say in my edit, and please edit your post to enclose the output between code tags.

I'll get back later.

---

### Post by Shaggin Shea on 2011-11-07
I remember that when I was setting up this ubuntu usb that it was my intention to use persistent. I am 98% sure I did this. Any way I can verify for you that persistent mode is on?

Some additional things have come to my attention which may help diagnose this problem.

Mounting of different things are also buggy.

CD: Gave me mount error 16 but actually mounted the drive?
USB: Same as CD

Then when I try to safely remove ubuntu tells me I can not remove them because they are busy.
Unable to stop drive
Failed to eject media; one or more volumes on the media are busy.

---

### Post by coffeecat on 2011-11-07
> **Shaggin Shea said:**
> Any way I can verify for you that persistent mode is on?

Perhaps you might want to verify for yourself! :wink:

Plug your live USB pendrive into any running OS. It doesn't have to be Ubuntu; you can use Windows or even MacOS. The pendrive is formatted FAT32 so anything can read it. Have a look for a file called casper-rw in the root of the filesystem. It will be as big as the size of your persistence. If present, it will be with the files called autorun.inf, ldlinux.sys, wubi.exe, md5sum.txt and README.diskdefines. If casper-rw is not there then you do not have persistence.

---

### Post by Shaggin Shea on 2011-11-07
:P casper-rw properties 3.99 GB (4,287,627,264 bytes)

---

### Post by coffeecat on 2011-11-07
Curious that your /etc/fstab line didn't stick. Try this in the live session:

```

sudo mkdir /media/HP
gksu gedit /etc/fstab
```

Add this line:

```
UUID=CE469F4C469F33E5     /media/HP     ntfs     defaults,nls=iso8859-1,uid=999,umask=000,windows_names  0 0
```

You can change /media/HP to /media/WindowsNTFS if you want. I prefer the mountpoint to be the same as the partition label, but it doesn't have to be.

uid=999 because the UID of the ubuntu account is 999 in the live session, not the 1000 the first user would be in a permanent installation.

Save the edited /etc/fstab, and then:

```
sudo mount -a
```

What happens? Reboot. What happens?

---

### Post by Shaggin Shea on 2011-11-07
```
ubuntu@ubuntu:~$ gksu gedit /etc/fstab

(gedit:4941): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.V24L4V': No such file or directory

(gedit:4941): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:4941): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.IGJS4V': No such file or directory

(gedit:4941): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory
```

Reboot, no change.

---

### Post by coffeecat on 2011-11-07
Opening gedit with gksu or gksudo has caused blood-curdling errors since time immemorial. I always ignore them!

---

### Post by Shaggin Shea on 2011-11-08
Bump

---

### Post by Shaggin Shea on 2011-11-09
bump

---

### Post by coffeecat on 2011-11-09
There's no point bumping this thread without saying whether or not the line I suggested you add to /etc/fstab worked.

---


---
title: "Copy files from USB in Ubuntu 10.10"
date: 2010-11-21
forum: General Help
---

### Post by DaveReed on 2010-11-21
In order to install gnome-ppp and wvdial I had to download six .deb files via Windows and I now have them on a USB stick.  I have the folder open on my Ubuntu 10.10 desktop as /66 MB Filesystem/LinuxDOWNLOADS/gnome-ppp and I'm trying to copy or drag-and-drop the files to /var/cache/apt/archives so I can install them.

It won't allow me to paste or to drag-and-drop, probably because I don't have root privileges when I'm operating as Ubuntu.

It will be a real pain to try to do this via a command line using sudo, but I suppose that is the only alternative.  Is that right?

But how can I find the files via the command line?  The open window says they are at /66 MB Filesystem/LinuxDOWNLOADS/gnome-ppp, but the terminal says "No such file or directory."

Sorry to be such a newbie, but alas that is where I find myself.

Thanks,
Dave

---

### Post by papibe on 2010-11-21
First, I want to double check where the USB stick is mounted. Could you post the result of these commands:
```
$ sudo mount -l
$ sudo fdisk -l
```
Regards.

---

### Post by uRock on 2010-11-21
Can you double click them where they are and install them using the Ubuntu Software Center.

---

### Post by DaveReed on 2010-11-22
> **papibe said:**
> First, I want to double check where the USB stick is mounted. Could you post the result of these commands:
```
$ sudo mount -l
$ sudo fdisk -l
```Regards.
Thank you, papibe, for taking the time to help me with this.  Sorry about the delay.

Those commands resulted in this output:

ubuntu@ubuntu:~$ sudo mount -l
aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
/dev/sdb1 on /cdrom type vfat (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda1 on /media/E0B4A04EB4A028CC type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdc1 on /media/A070-CD22 type vfat (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9f939f93

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3647    29294496    7  HPFS/NTFS

Disk /dev/sdb: 7998 MB, 7998537728 bytes
247 heads, 62 sectors/track, 1020 cylinders
Units = cylinders of 15314 * 512 = 7840768 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00054872

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1020     7810109    c  W95 FAT32 (LBA)

Disk /dev/sdc: 66 MB, 66060288 bytes
16 heads, 32 sectors/track, 252 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x56203109

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         251       64240    6  FAT16
ubuntu@ubuntu:~$ 

I can see that the USB disk with the files is /dev/sdc 
And my hard drive must be /dev/sda1

And I can reach both via the GUI (which won't let me drag and drop to /var/cache/apt/archives) but not via the terminal window.

Thanks,
Dave

---

### Post by DaveReed on 2010-11-22
> **uRock said:**
> Can you double click them where they are and install them using the Ubuntu Software Center.
Thank you, uRock, for that suggestion.  I have the files now on my Windows hard drive as well as on the USB stick.  

When I double-click them, the Ubutnu Software Center opens up and says, "Please install Wvdial' via your normal software channels.  Only install this file if you trust the origin."--which seems to suggest that I should be able to install it.  

But when I click the "Install" button, an "Installing..." progress bar appears, and then after clocking for a while, a message appears:

"Failed to download package files.  Check your Internet connection."

Thanks,
Dave

---

### Post by papibe on 2010-11-22
Your USB stick is mounted on /media/A070-CD22. Try this:
```
$ cd
$ mkdir mypackages
$ cd mypackages
$ cp -r /media/A070-CD22/* .
```
Then try to install the packages from mypackages. This should solve the problems with the permissions since you have read/write permission in your home directory.

Regards.

---

### Post by DaveReed on 2010-11-23
Thank you both for your help.  I ended up playing with the Synaptic Package Manager (which was completely new to me) and found out how to make it look inside the USB stick.  It then installed from there.

Thanks,
Dave

---


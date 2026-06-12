---
title: "unplugging usb hard drive"
date: 2010-11-13
forum: General Help
---

### Post by petersull on 2010-11-13
Hi, can someone please explain about unplugging a usb hard drive. How should I do it? How do I know whether it has stopped? Do I have to click on something before I unplug it?

I have an old usb 30 gb HD with some important data on it. I have never had a problem with it before and have always just unplugged it when I had finished with it. Now I cannot get access to it any more.

Please help.

---

### Post by llawwehttam on 2010-11-13
It should be on the desktop so you can right click on the icon and press "Safely Remove"

You could also open "Computer" and do the same.


If you cannot get access to the usb drive any more you may have to re-format it I'm afraid.

Hope that helps,

Matt

---

### Post by blueridgedog on 2010-11-13
Can you post the output of 

```
lsusb
```

with the drive unplugged and then again with the drive plugged in?

---

### Post by efflandt on 2010-11-13
Also if it is actually assigned a /dev (see tail end of dmesg when you plug it in) does **sudo fdisk -l** (small L) still show it and its partitions.  If fdisk still shows it, maybe something got corrupted that may be able to be fixed (depending up type of file system).  If fdisk does not show it, there may be a more significant problem.

Especially if you have written something to it recently, it is best to at least unmount all partitions on it from nautilus or the desktop (or umount in terminal) which would flush any data in cache, if not Safely Remove or Eject by right clicking on it on desktop.

---

### Post by azertyh on 2010-11-13
hello,
on the desktop, right-click the usb and select unmount, ubuntu notifies you to unplug it.
if you are not sure that you have unmounted the usb, right-click again, there is mount instead of unmount.

---

### Post by petersull on 2010-11-13
Here are the results of lsusb without the external drive and then with.


psullivan@pete-pc-u:~$ lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
psullivan@pete-pc-u:~$ lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 13fd:1040 Initio Corporation 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
psullivan@pete-pc-u:~$ 

Regards,

Pete.

---

### Post by petersull on 2010-11-13
Here is the result of fdisk -l


psullivan@pete-pc-u:~$ sudo fdisk -l
[sudo] password for psullivan: 

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5661b9b7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1072     8610808+   7  HPFS/NTFS
/dev/sda2   *        1073        4890    30659364    7  HPFS/NTFS
/dev/sda3            4890        7296    19333121    5  Extended
/dev/sda5            4890        7190    18481152   83  Linux
/dev/sda6            7190        7296      850944   82  Linux swap / Solaris

Disk /dev/sdb: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6b14da15

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        3647    29294496    7  HPFS/NTFS
psullivan@pete-pc-u:~$ 

Regards,

Pete

---

### Post by petersull on 2010-11-13
This is the error message I get when I try to open the external drive

UNABLE TO MOUNT LOCATION

DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

---

### Post by blueridgedog on 2010-11-13
Do you only have one other disk?  If so, we can assume that /dev/sdb1 * 1 3647 29294496 7 HPFS/NTFS is the external.  

What is the output of 

```
mount
```

While the disk is plugged in?

lsusb shows that it is seen by the OS.

---

### Post by petersull on 2010-11-14
This is the output of mount

psullivan@pete-pc-u:~$ mount
/dev/sda5 on / type ext4 (rw,errors=remount-ro,commit=0)
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
gvfs-fuse-daemon on /home/psullivan/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=psullivan)
/dev/sda1 on /media/42187BB2187BA397 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda2 on /media/Windows_ type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
psullivan@pete-pc-u:~$

---

### Post by blueridgedog on 2010-11-14
What happens when you try and mount it manually:

```
sudo mkdir /mnt/usbdrive
sudo mount /dev/sdb1 /mnt/usbdrive
```

---

### Post by petersull on 2010-11-15
This is the result,

psullivan@pete-pc-u:~$ sudo mkdir /mnt/usbdrive
[sudo] password for psullivan: 
psullivan@pete-pc-u:~$ sudo mount /dev/sdb1 /mnt/usbdrive 
sudoFailed to write lock '/dev/sdb1': Resource temporarily unavailable
Error opening '/dev/sdb1': Resource temporarily unavailable
Failed to mount '/dev/sdb1': Resource temporarily unavailable
psullivan@pete-pc-u:~$

It does show in Computer as 30 GB Hard Disk: 30 GB Filesystem.

Regards,

Pete.

---

### Post by blueridgedog on 2010-11-15
Since you are running ntfs on the drive and have a windows partition, can you boot into windows?  If so, I suggest booting into windows and seeing if you can run chkdsk on the disk from within windows.

---

### Post by petersull on 2010-11-16
Hi,

Windows stops responding when I plug in the usb hard disk. So no joy there.

Please have a look at the following copied from terminal. It is the 30GB usb hard disk that I cannot use. Obviously it can be found on the system, so that would suggest that there is some hope to access some or all of the data on it. Can anyone suggest how I can progress from here.

psullivan@pete-pc-u:~$ sudo fdisk -l
[sudo] password for psullivan: 

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5661b9b7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1072     8610808+   7  HPFS/NTFS
/dev/sda2   *        1073        4890    30659364    7  HPFS/NTFS
/dev/sda3            4890        7296    19333121    5  Extended
/dev/sda5            4890        7190    18481152   83  Linux
/dev/sda6            7190        7296      850944   82  Linux swap / Solaris

Disk /dev/sdb: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6b14da15

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        3647    29294496    7  HPFS/NTFS
psullivan@pete-pc-u:~$ fsck /dev/sdb1
fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)
fsck.ext2: Permission denied while trying to open /dev/sdb1
You must have r/w access to the filesystem or be root
psullivan@pete-pc-u:~$ fsck /dev/sdb
fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)
fsck.ext2: Permission denied while trying to open /dev/sdb
You must have r/w access to the filesystem or be root
psullivan@pete-pc-u:~$

---

### Post by blueridgedog on 2010-11-17
ok, how about

```
sudo fsck /dev/sdb1
```

This assumes you have ntfs-3g installed, if not then precede that with:

```
sudo apt-get install ntfs-3g
```

---

### Post by petersull on 2010-11-17
Thanks for that.

What does the following mean?

Seems to me it has ntfs-3g installed, but then can't find it.


psullivan@pete-pc-u:~$ sudo fsck /dev/sdb1
[sudo] password for psullivan: 
fsck from util-linux-ng 2.17.2
fsck: fsck.ntfs: not found
fsck: Error 2 while executing fsck.ntfs for /dev/sdb1
psullivan@pete-pc-u:~$ sudo apt-get install ntfs-3g
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ntfs-3g is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.
psullivan@pete-pc-u:~$ sudo fsck /dev/sdb1
fsck from util-linux-ng 2.17.2
fsck: fsck.ntfs: not found
fsck: Error 2 while executing fsck.ntfs for /dev/sdb1
psullivan@pete-pc-u:~$ sudo fsck /dev/sdb1
fsck from util-linux-ng 2.17.2
fsck: fsck.ntfs: not found
fsck: Error 2 while executing fsck.ntfs for /dev/sdb1
psullivan@pete-pc-u:~$ sudo apt-get install ntfs-3g
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ntfs-3g is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.
psullivan@pete-pc-u:~$

---

### Post by petersull on 2010-11-17
Here is another error massage that comes up.

Unable to mount 30 GB Filesystem

Error mounting: mount exited with exit code 13: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read NTFS $Bitmap: Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

As I mentioned before, Windows stops responding when the drive is plugged in.

---

### Post by blueridgedog on 2010-11-17
Ok, the tool installed by ntfs-3g goes by another name.  Try:

```
sudo ntfsfix /dev/sdb1
```

---

### Post by petersull on 2010-11-17
Two results here. The first was when the drive was still busy trying to mount or something. The second I did after it had finally reported that it was unable to mount.


psullivan@pete-pc-u:~$ sudo ntfsfix /dev/sdb1
[sudo] password for psullivan: 
Mounting volume... Error opening partition device: Resource temporarily unavailable.
Failed to startup volume: Resource temporarily unavailable.
FAILED
Attempting to correct errors... Error opening partition device: Resource temporarily unavailable.
FAILED
Failed to startup volume: Resource temporarily unavailable.
Volume is corrupt. You should run chkdsk.

psullivan@pete-pc-u:~$ sudo ntfsfix /dev/sdb1
Mounting volume... pread: Input/output error
Failed to calculate number of free MFTs: Input/output error.
FAILED
Attempting to correct errors... 
Processing $MFT and $MFTMirr...
Reading $MFT... OK
Reading $MFTMirr... OK
Comparing $MFTMirr to $MFT... OK
Processing of $MFT and $MFTMirr completed successfully.
Setting required flags on partition... OK
Going to empty the journal ($LogFile)... OK
pread: Input/output error
Failed to calculate number of free MFTs: Input/output error.
Remount failed: Input/output error.
psullivan@pete-pc-u:~$

---

### Post by lumore22 on 2010-11-17
Greetings-

I had a similar problem with my new ( now old) install of Lucid.  When I tried to access it again, I did not get the icon on the desktop.

My USB drive was previously used on a Windows system. I don't know if this is the case for
you.

I had to remount my USB drive after I unplugged it the first time. To do this, you have to be in sudo mode.  sudo -i will get you there.
. 
 Also, there is documentation on the forums on how to do this - remounting a USB drive.  Access it 

Regards-

---

### Post by lumore22 on 2010-11-17
Sorry forgot to give you the sequence of commands that I entered and which finally worked for me.

1. create a mountpoint
    mkdir /media/external
2. mount
     sudo   mount -t vfat /dev/sdb1 /media/external -o uid=1000, gid=100,utf8,dmask=027, fmask=137

Previously I tried unsuccessfully

3. sudo mount -t ntfs-3g /dev/sdb1 /media/external

** Be careful when using options preceded by a " - ".  In ntfs-3g, I don't remember if there should be a space between "ntfs" and -3g or not. 

Good luck!

---

### Post by blueridgedog on 2010-11-17
> **petersull said:**
> 
pread: Input/output error
Failed to calculate number of free MFTs: Input/output error.
Remount failed: Input/output error.
psullivan@pete-pc-u:~$

Try the same command using a different USB port on the PC and a different cable (if you have one).  At this point I am thinking you have a hardware issue (cable/port/external enclosure/drive).

---


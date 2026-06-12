---
title: "Set up home on a separate partition/drive &amp; can't add new users"
date: 2012-03-22
forum: General Help
---

### Post by LOQ on 2012-03-22
I followed the directions [here]("https://help.ubuntu.com/community/Partitioning/Home/Moving") to move the /home directory to a separate partition (actually a separate drive) in Ubuntu 11.10.  The reason for doing so was because I'm booting from a 64gb ssd and put /home on a 2tb hdd. 

For some reason, now the owner of the /home directory is the main user on the system (group is that named after such user), rather than root.  Additionally, when I create new users with the newuser command (or from the GUI), they appear in the login screen but can't seem to log in.  The only user that can is the main user.  The new users also don't seem to have home directories.  

When I change the owner of /home to root:root with chown (seems to be how it's set up on my laptop with 12.04 beta), no users can log in, including the main user.  Logging in as any user from terminal starts in the root directory and gives a "permission denied" error when doing ```
cd ~
``` or ```
cd /home/USER
```.  As of now, I've switched the owner of /home back to the main user and now can at least log in as that user.

Any help or guidance would be greatly appreciated.  I'm fairly new with ubuntu and linux generally but I've enjoyed using it enough to build a couple HTPCs running ubuntu/xbmc (windows in a virtual machine for netflix on the main one), a print/backup server with just ubuntu, and a hardware firewall with pfsense, so I'm not totally helpless but am perplexed by this issue.

Thanks in advance.

---

### Post by papibe on 2012-03-22
Hi LOQ.

In order to make a suggestion it would be valuable to know some details about your current configuration.

Could you post the content of the file /etc/fstab ?

Also, could you post the result of these commands too?
```
sudo fdisk -l

mount -l

df -h
```
Please paste your results using the code tags (#) available when you reply a post.

Regards.

---

### Post by Bucky Ball on 2012-03-22
It appears you are using 12.04 LTS. This is still testing and not released yet so expect breakages and idiosyncracies (and this is possibly one of them). Might be worth a bug report (one might already exist) if you can't get things sorted. ;)

---

### Post by LOQ on 2012-03-23
I'm running 12.04 on my personal laptop.  The HTPCs, including the one in question, are running 11.10.  Thanks for the quick responses by the way.  Didn't realize it didn't automatically subscribe you to your own posts or I'd have replied sooner.

First, my fstab.  Sorry for the extra, commented out stuff.  Had tried a couple things and hadn't gotten them to work yet.  I'd also changed the entries to all UUIDs when I switched my home partition, so I've also included below the results of blkid as well.

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0

# / was on /dev/sda1 during installation = Boot
UUID=0ed84776-8082-4aad-96db-1a6fd76e06d2    /    ext4    noatime,discard,errors=remount-ro    0    1

# swap was on /dev/sda5 during installation
UUID=bc7d4768-2b04-4f6c-bda7-c8c0d897c0ca none            swap    sw              0       0

#/tmp mounted in ram, supposed to speed up the ssd
#tmpfs    /tmp    tmpfs    nodev,nosuid,noexed,mode=1777    0    0
#tmpfs    /tmp    tmpfs    defaults,noatime,mode=1777    0    0

#Home as 2tb drive
UUID=468e9b30-e7b1-4e99-962f-960df4d99d49    /home ext4    nodev,nosuid    0    2

#Old Bootable hard drive
UUID=c2bf0c21-b380-40d2-ad32-0900bb53863d    /media/OldSys    ext4    defaults,errors=remount-ro    0    0

#1TB, NTFS
#ripped DVDs
#UUID=7E6094DC60949D09    /home/michael/Videos/DVDs    ntfs-3g    defaults,locale=en_US.UTF-8    0    3

#Floppy Disk = automatically created
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```The others:
```

$ blkid
/dev/sda1: UUID="0ed84776-8082-4aad-96db-1a6fd76e06d2" TYPE="ext4" 
/dev/sda5: UUID="bc7d4768-2b04-4f6c-bda7-c8c0d897c0ca" TYPE="swap" 
/dev/sdb1: UUID="c2bf0c21-b380-40d2-ad32-0900bb53863d" TYPE="ext4" 
/dev/sdb5: UUID="7d7033f5-1754-4bc2-9476-e920536c8a65" TYPE="swap" 
/dev/sdc1: LABEL="BeastBackup" UUID="468e9b30-e7b1-4e99-962f-960df4d99d49" TYPE="ext4" 
/dev/sdd1: LABEL="Beast_2" UUID="7E6094DC60949D09" TYPE="ntfs" 
``````
$ sudo fdisk -l

Disk /dev/sda: 64.0 GB, 64023257088 bytes
255 heads, 63 sectors/track, 7783 cylinders, total 125045424 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000cad17

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   108271615    54134784   83  Linux
/dev/sda2       108273662   125044735     8385537    5  Extended
/dev/sda5       108273664   125044735     8385536   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006924c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63  1929743864   964871901   83  Linux
/dev/sdb2      1929743865  1953520064    11888100    5  Extended
/dev/sdb5      1929743928  1953520064    11888068+  82  Linux swap / Solaris

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000aeb79

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63  3907024064  1953512001   83  Linux

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa354011a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1              63  1953520064   976760001    7  HPFS/NTFS/exFAT
``````

$ mount -l
/dev/sda1 on / type ext4 (rw,noatime,discard,errors=remount-ro,commit=0)
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
/dev/sdb1 on /media/OldSys type ext4 (rw,errors=remount-ro,commit=0)
/dev/sdc1 on /home type ext4 (rw,nosuid,nodev,commit=0) [BeastBackup]
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/michael/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=michael)
/dev/sr0 on /media/BOARDWALK_EMPIRE_S1_DISC1 type udf (ro,nosuid,nodev,uid=1000,gid=1000,iocharset=utf8,umask=0077,dmode=0500,uhelper=udisks) [BOARDWALK_EMPIRE_S1_DISC1]
``````
$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              51G  5.1G   44G  11% /
udev                  3.9G  4.0K  3.9G   1% /dev
tmpfs                 1.6G  1.4M  1.6G   1% /run
none                  5.0M     0  5.0M   0% /run/lock
none                  4.0G  244K  4.0G   1% /run/shm
/dev/sdb1             906G  754G  107G  88% /media/OldSys
/dev/sdc1             1.8T  1.5T  222G  88% /home
/dev/sr0              7.2G  7.2G     0 100% /media/BOARDWALK_EMPIRE_S1_DISC1
```

---

### Post by papibe on 2012-03-23
Thanks.

The only thing that I see different from my systems that have a separate /home partition is that they are mounted just with the option 'defaults'

Try it out, and let us know:
```
#Home as 2tb drive
UUID=468e9b30-e7b1-4e99-962f-960df4d99d49   /home ext4   **defaults**   0    2
```
Regards.

---

### Post by LOQ on 2012-03-28
Thanks for the advice.  Ubuntu is now loading much faster (i.e. back to the speeds before I added the new users), but I still can't log in as either new user.  

Is there any detriment to using deluser/adduser to hopefully generate the required default files for new users?  Any good resources on users/UIDs?  I remember reading about NFS and how UIDs are the ultimate determinant of access, rather than username.  Is this something to worry about more generally?

---

### Post by oldfred on 2012-03-28
Have you checked ownership & permissions? Sometimes a move messes with dmrc settings also.

Sometimes there are dmrc errors or permission errors and this has how to correct them:
[https://help.ubuntu.com/community/dmrcErrors](https://help.ubuntu.com/community/dmrcErrors)
#Replace all instances of username with your login name or use $USER
sudo chown username:username /home/username/.dmrc
chmod 644 /home/username/.dmrc
sudo chown username:username /home/username     
chmod 755 /home/username

.dmrc errors- drs305
[http://ubuntuforums.org/showthread.php?p=6161267](http://ubuntuforums.org/showthread.php?p=6161267)
.ICEauthority errors
[http://ubuntuforums.org/showthread.php?t=1590835](http://ubuntuforums.org/showthread.php?t=1590835)
sudo chown $USER:$USER /home/username/.ICEauthority
sudo chmod 644 /home/username/.ICEauthority
sudo chmod 644 $HOME/.ICEauthority
look at the permissions on ~/.Xauthority, too. It often gets changed when ~/.ICEauthority gets changed. The same fix applies.

---

### Post by LOQ on 2012-03-28
The weird thing is, neither of the new users even have those files.  The most recent added user doesn't even have a home directory.  The other does but the only file is "examples.desktop."  I believe there are no hidden files either but I'll have to check for certain when I get home.

---


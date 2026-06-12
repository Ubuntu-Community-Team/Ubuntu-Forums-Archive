---
title: "HDD mounting problem"
date: 2010-06-12
forum: General Help
---

### Post by cqc on 2010-06-12
I have apacer 320 GB new HDD, format is NTFS. Everything worked fine till today when i tride to muont it (it should mount on boot but it didnt) i got this message:
```
Error mounting: mount exited with exit code 1: helper failed with:
Unprivileged user can not mount NTFS block devices using the external FUSE
library. Either mount the volume as root, or rebuild NTFS-3G with integrated
FUSE support and make it setuid root. Please see more information at
http://ntfs-3g.org/support.html#unprivileged
```
i Tried to mount it with Storage device manager and with NTFS conf. tool, but nothing happpend. What to do?
Thanks
by the way my local ubuntu forum is down right now :sad:, im so pissed :mad:

---

### Post by Morbius1 on 2010-06-12
Please post the output of the following commands:

```
sudo blkid -c /dev/null
cat /etc/fstab
mount
```

---

### Post by cqc on 2010-06-12
> **Morbius1 said:**
> Please post the output of the following commands:

```
sudo blkid -c /dev/null
cat /etc/fstab
mount
```
```
stojak@ubuntu:~$ sudo blkid -c /dev/null
[sudo] password for stojak: 
/dev/loop0: UUID="85c907c9-2bfe-4a57-ae6d-6130dbc1297a" TYPE="ext4" 
/dev/sda1: UUID="CEF48B78F48B6217" TYPE="ntfs" 
/dev/sdb1: LABEL="disk" UUID="56249DAD17252AE8" TYPE="ntfs" 
stojak@ubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
/dev/sda1    /host    ntfs-3g    defaults,nosuid,nodev,locale=sr_RS.utf8@latin    00
/dev/sdb1    /media/sdb1    ntfs-3g    defaults,users,locale=sr_RS.utf8@latin    00
/dev/sdd1    /media/disk_    ntfs    defaults,nls=utf8,umask=0222    0    0
/dev/sdc1    /media/disk    ntfs-3g    defaults,nosuid,nodev,locale=sr_RS.utf8@latin    0    0
/host/ubuntu/disks/root.disk    /    ext4    loop,errors=remount-ro    0    1
/host/ubuntu/disks/swap.disk    none    swap    loop,sw    0    0


stojak@ubuntu:~$ mount
/dev/loop0 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/sda1 on /host type fuseblk (rw,nosuid,nodev,locale=sr_RS.utf8@latin)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/stojak/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=stojak)
stojak@ubuntu:~$ ^C
stojak@ubuntu:~$ 

```
sdb1 is the problem

---

### Post by Morbius1 on 2010-06-12
You and I have a problem. This appears to be a Wubi install ( install within Windows ) not a "real" install. I have no experience with Wubi installs.

But I can tell you that the "users" option in a "real" install in this line will not work as you expect it to and is probably the source of the error message:
>  /dev/sdb1    /media/sdb1    ntfs-3g    defaults,[COLOR=Blue]users[/COLOR],locale=sr_RS.utf8@latin    00I would open a Terminal and edit fstab as root: 
```
gksu gedit /etc/fstab
```And get rid of that option so that it looks like this:
> /dev/sdb1    /media/sdb1    ntfs-3g    defaults,locale=sr_RS.utf8@latin     0 0Then save the file, exit gedit, and back in the Terminal type:
```
sudo mount -a
```The only other problem is this in fstab:
> /dev/sdd1    /media/disk_    ntfs    defaults,nls=utf8,umask=0222    0    0
/dev/sdc1    /media/disk    ntfs-3g    defaults,nosuid,nodev,locale=sr_RS.utf8@latin    0    0
There's no reference to those partitions in the blkid command. Do you know what they are?

---

### Post by cqc on 2010-06-12
> **Morbius1 said:**
> You and I have a problem. This appears to be a Wubi install ( install within Windows ) not a "real" install. I have no experience with Wubi installs.

But I can tell you that the "users" option in a "real" install in this line will not work as you expect it to and is probably the source of the error message:
I would open a Terminal and edit fstab as root: 
```
gksu gedit /etc/fstab
```And get rid of that option so that it looks like this:
Then save the file, exit gedit, and back in the Terminal type:
```
sudo mount -a
```The only other problem is this in fstab:
There's no reference to those partitions in the blkid command. Do you know what they are?
I installed ubuntu in win using Wubi. I edited that line so it could mount on boot. Those two partitions are the same sdb1, because i formated my hdd a couple of times and gave him those names... then i used storage device manager... had a lot of problems

i edited line as you told me and deleted those two 'old' lines and got this with sudo mount -a:
> stojak@ubuntu:~$ sudo mount -a
$MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

any ideas?

---

### Post by Morbius1 on 2010-06-12
So this is solved?

---

### Post by cqc on 2010-06-12
no
> i edited line as  you told me and deleted those two 'old' lines and got this with sudo  mount -a:
 	Quote:
 	 	 		 			 				stojak@ubuntu:~$ sudo mount -a
$MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details. 			 		 	 	 
any ideas? 		                   		  		  		  		  		 		 			 				

---

### Post by Morbius1 on 2010-06-12
Can you post the fstab again please:

```
cat /etc/fstab
```

---

### Post by cqc on 2010-06-12
fstab
```
stojak@ubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
/dev/sda1    /host    ntfs-3g    defaults,nosuid,nodev,locale=sr_RS.utf8@latin    00
/dev/sdb1 /media/sdb1 ntfs-3g defaults,locale=sr_RS.utf8@latin 0 0 

/host/ubuntu/disks/root.disk    /    ext4    loop,errors=remount-ro    0    1
/host/ubuntu/disks/swap.disk    none    swap    loop,sw    0    0


```

---

### Post by Morbius1 on 2010-06-12
Make this:
> /dev/sdb1 /media/sdb1 ntfs-3g defaults,locale=sr_RS.utf8@latin 0 0 Look like this:
> /dev/sdb1 /media/sdb1 ntfs-3g defaults,nosuid,nodev,locale=sr_RS.utf8@latin 0 0Then :
```
sudo mount -a
```

---

### Post by cqc on 2010-06-12
> **Morbius1 said:**
> Make this:
Look like this:
Then :
```
sudo mount -a
```
i got same message :(

---

### Post by Morbius1 on 2010-06-12
The only thing I can think of is to go back into fstab and comment out the sdb1 line until either I or someone who knows something about Wubi knows what the problem is here. It almost sounds like a hardware problem.

Just put a # sign in front of the /dev/sdb1 line so that it looks like this:
>  #/dev/sdb1 /media/sdb1 ntfs-3g  defaults,nosuid,nodev,locale=sr_RS.utf8@latin 0 0                      Then do the **sudo mount -a **again and make sure there are no errors reported. This will disable the mounting of sdb1.

---

### Post by cqc on 2010-06-12
HDD is working fine on windows

---

### Post by cqc on 2010-06-12
tried to mount it with disk manager and got this: 
Error mounting: mount exited with exit code 1: helper failed with:
mount: only root can mount /dev/sdb1 on /media/disk
what to do?

---

### Post by cqc on 2010-06-13
when i got this message:
```
Error mounting: mount exited with exit code 1: helper failed with:
Unprivileged user can not mount NTFS block devices using the external FUSE
library. Either mount the volume as root, or rebuild NTFS-3G with integrated
FUSE support and make it setuid root. Please see more information at
http://ntfs-3g.org/support.html#unprivileged

```
i checked out [http://www.tuxera.com/community/ntfs-3g-faq/#unprivileged](http://www.tuxera.com/community/ntfs-3g-faq/#unprivileged) to see what i can find this is what is says: 
```
**Why can’t unprivileged**  users mount block devices? or
 **Why do I get “fusermount: option  blkdev is privileged” error?** Unprivileged block device mounts work only if all the below  requirements are met:
 
[LIST=1]
[*]ntfs-3g is compiled with integrated FUSE support
[*]the ntfs-3g binary is at least version 1.2506
[*]the ntfs-3g binary is set to setuid-root
[*]the user has access right to the volume
[*]the user has access right to the mount point
[/LIST]
 The root user can make an ntfs-3g binary setuid-root as shown below
chown root $(which ntfs-3g)
chmod 4755 $(which ntfs-3g) In such case the driver will also be  able
 
[LIST]
[*]to fix common FUSE kernel module loading problems
[*]to create the required but sometimes incorrectly removed or missing  FUSE device file
[/LIST]
 Please note that using setuid-root can result unforeseen privilege  escalation and its usage is discouraged. Only the absolutely trusted  users must be granted such access. Below is an example how this can be  done for users in the ntfsuser group to be able to mount any NTFS volume  if they have also the needed volume access rights.  chown  root.ntfsuser $(which ntfs-3g)
chmod 4750 $(which ntfs-3g) The setuid-root ntfs-3g driver applies  the principle of least privilege during its lifetime as a safety  measure.


```
im not sure what to do? can this help? please help

---

### Post by cqc on 2010-06-13
i formated hdd in win and works now... dont know why. anyway can hight temperature affect hdd it is hot here 39 C uff

---


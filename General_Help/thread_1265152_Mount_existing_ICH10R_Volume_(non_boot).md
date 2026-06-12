---
title: "Mount existing ICH10R Volume (non boot)"
date: 2009-09-13
forum: General Help
---

### Post by agent20x on 2009-09-13
I just installed 9.04 on a seperate drive from my existing raid 5 array on my fakeraid setup and I am unable to mount the volume.

I have 4 disks. 1 where all my OSs are installed (xp and Ubuntu) and the other 3 are the volume setup by the ICH10R.

I installed dmraid but have been unsuccessful trying to mount it.

I'm not sure what a lot of this means but I think it is important.

```
#ls -l /dev/mapper
total 0
crw-rw---- 1 root root  10, 61 2009-09-12 15:41 control
brw-rw---- 1 root disk 252,  0 2009-09-12 23:05 isw_bjhfihdefe_Storage

#sudo mount -t ntfs /dev/mapper/isw_bjhfihdefe_Storage /raid
Failed to read bootsector (size=0)
Failed to mount '/dev/mapper/isw_bjhfihdefe_Storage': Invalid argument
The device '/dev/mapper/isw_bjhfihdefe_Storage' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0a630a63

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      121601   976760001    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0a630a64

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000007

Disk /dev/sdc doesn't contain a valid partition table

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc1e8c1e8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       41679   334786536    7  HPFS/NTFS
/dev/sdd2           41680       58700   136721182+  83  Linux
/dev/sdd3           58701       59065     2931862+  82  Linux swap / Solaris
/dev/sdd4           59066       60801    13944420    5  Extended
/dev/sdd5           59066       60801    13944388+   b  W95 FAT32


#sudo dmraid -r
/dev/sdc: isw, "isw_bjhfihdefe", GROUP, ok, 976773165 sectors, data@ 0
/dev/sdb: isw, "isw_bjhfihdefe", GROUP, ok, 976773165 sectors, data@ 0
/dev/sda: isw, "isw_bjhfihdefe", GROUP, ok, 976773165 sectors, data@ 0


#sudo dmraid -tay
isw_bjhfihdefe_Storage: 0 1953536512 raid45 core 2 131072 nosync raid5_la 1 256 3 -1207081360 /dev/sda 0 /dev/sdb 0 /dev/sdc 0
ERROR: dos: reading /dev/mapper/isw_bjhfihdefe_Storage[No such file or directory]
```

---

### Post by ronparent on 2009-09-13
Your output of **ls /dev/mapper** indicates your have unpartitioned raid volume isw_bjhfihdefe_Storage. Is this correct?

Edit: I didn't read closely enough the first time. I don't believe your mount command especially with nonexistent file specs will work for an unpartitioned drive. Once partitioned, the individual partitions - the ones for the symbolic links ending in numerals - will be mountable. Also did you create the /raid location in the file system. That is prerequisite for the mount command to work. Such a location will have to be created for each raid partition you wish to mount.

---

### Post by biebel on 2009-09-13
It is a known bug.
The patch is posted in the bugreport:[https://bugs.launchpad.net/ubuntu/+source/dmraid/+bug/356503](https://bugs.launchpad.net/ubuntu/+source/dmraid/+bug/356503)

---

### Post by agent20x on 2009-09-13
> **ronparent said:**
> Your output of **ls /dev/mapper** indicates your have unpartitioned raid volume isw_bjhfihdefe_Storage. Is this correct?

Edit: I didn't read closely enough the first time. I don't believe your mount command especially with nonexistent file specs will work for an unpartitioned drive. Once partitioned, the individual partitions - the ones for the symbolic links ending in numerals - will be mountable. Also did you create the /raid location in the file system. That is prerequisite for the mount command to work. Such a location will have to be created for each raid partition you wish to mount.

Its definitely partitioned. I just checked it right now with windows to make sure im not crazy

---

### Post by biebel on 2009-09-13
As I said in my previous post it is a known bug and the fix is in that bugreport.
Relevant posts:
> 
I have looked through the hooks and I can see there is a typo in the dmraid hook file.

Open up /usr/share/initramfs-tools/hooks/dmraid, so:
sudo gedit /usr/share/initramfs-tools/hooks/dmraid

look through that file, on line 23 it says force_load dm-raid45. This should of course be dm-raid4-5.

So if you change that to dm-raid4-5 then save it and update the initramfs with the above command* it should work.
> 
danwood76, nice catch! Some missing QA there. It would also need to be corrected in /sbin/dmraid-activate. Can you please make a debdiff for Jaunty, this should be SRU'ed as well.


[edit]
*That command above is sudo update-initramfs -u -k all
[/edit]

---

### Post by ronparent on 2009-09-13
Problem found - but you won't like it! If you do **dmraid -l** you will find that isw does not support raid5. Sorry, I don't know where we can go from here.

---

### Post by biebel on 2009-09-13
Good find and as usual I was skipping the basic diagnostic steps :/

Since having a similar problem (with my nvidia fakeraid) and the "ERROR: dos: reading /dev/mapper/...." error since jaunty I assumed it was the same bug.

My bad

---

### Post by ronparent on 2009-09-13
bieble: Actually the bug report refers to a problem with dmraid not activating raid on boot. Since I have been having that problem with another box I found it very helpful and am happy you posted it. Hang in there.

---

### Post by agent20x on 2009-09-13
ok I fixed the file at /usr/share/initramfs-tools/hooks/dmraid
I was unable to find a similar line in /sbin/dmraid-activate
Still no luck.

However, I was able to get it working with the Live CD (using it right now) with the following commands.

```
$ sudo modprobe dm-raid4-5 
$ sudo apt-get install -y dmraid 
$ sudo dmraid -ay

```ls -l /dev/mapper ouput:
total 0
crw-rw---- 1 root root  10, 61 2009-09-13 15:31 control
brw-rw---- 1 root disk 252,  0 2009-09-13 22:48 isw_bjhfihdefe_Storage
brw-rw---- 1 root disk 252,  1 2009-09-13 22:52 isw_bjhfihdefe_Storage1

sudo dmraid -ay -vvv -d output:
WARN: locking /var/lock/dmraid/.lock
NOTICE: skipping removable device /dev/sde
NOTICE: skipping removable device /dev/sdf
NOTICE: skipping removable device /dev/sdg
NOTICE: skipping removable device /dev/sdh
NOTICE: /dev/sdd: asr     discovering
NOTICE: /dev/sdd: ddf1    discovering
NOTICE: /dev/sdd: hpt37x  discovering
NOTICE: /dev/sdd: hpt45x  discovering
NOTICE: /dev/sdd: isw     discovering
NOTICE: /dev/sdd: jmicron discovering
NOTICE: /dev/sdd: lsi     discovering
NOTICE: /dev/sdd: nvidia  discovering
NOTICE: /dev/sdd: pdc     discovering
NOTICE: /dev/sdd: sil     discovering
NOTICE: /dev/sdd: via     discovering
NOTICE: /dev/sdc: asr     discovering
NOTICE: /dev/sdc: ddf1    discovering
NOTICE: /dev/sdc: hpt37x  discovering
NOTICE: /dev/sdc: hpt45x  discovering
NOTICE: /dev/sdc: isw     discovering
NOTICE: /dev/sdc: isw metadata discovered
NOTICE: /dev/sdc: jmicron discovering
NOTICE: /dev/sdc: lsi     discovering
NOTICE: /dev/sdc: nvidia  discovering
NOTICE: /dev/sdc: pdc     discovering
NOTICE: /dev/sdc: sil     discovering
NOTICE: /dev/sdc: via     discovering
NOTICE: /dev/sdb: asr     discovering
NOTICE: /dev/sdb: ddf1    discovering
NOTICE: /dev/sdb: hpt37x  discovering
NOTICE: /dev/sdb: hpt45x  discovering
NOTICE: /dev/sdb: isw     discovering
NOTICE: /dev/sdb: isw metadata discovered
NOTICE: /dev/sdb: jmicron discovering
NOTICE: /dev/sdb: lsi     discovering
NOTICE: /dev/sdb: nvidia  discovering
NOTICE: /dev/sdb: pdc     discovering
NOTICE: /dev/sdb: sil     discovering
NOTICE: /dev/sdb: via     discovering
NOTICE: /dev/sda: asr     discovering
NOTICE: /dev/sda: ddf1    discovering
NOTICE: /dev/sda: hpt37x  discovering
NOTICE: /dev/sda: hpt45x  discovering
NOTICE: /dev/sda: isw     discovering
NOTICE: /dev/sda: isw metadata discovered
NOTICE: /dev/sda: jmicron discovering
NOTICE: /dev/sda: lsi     discovering
NOTICE: /dev/sda: nvidia  discovering
NOTICE: /dev/sda: pdc     discovering
NOTICE: /dev/sda: sil     discovering
NOTICE: /dev/sda: via     discovering
DEBUG: _find_set: searching isw_bjhfihdefe
DEBUG: _find_set: not found isw_bjhfihdefe
DEBUG: _find_set: searching isw_bjhfihdefe_Storage
DEBUG: _find_set: searching isw_bjhfihdefe_Storage
DEBUG: _find_set: not found isw_bjhfihdefe_Storage
DEBUG: _find_set: not found isw_bjhfihdefe_Storage
NOTICE: added /dev/sdc to RAID set "isw_bjhfihdefe"
DEBUG: _find_set: searching isw_bjhfihdefe
DEBUG: _find_set: found isw_bjhfihdefe
DEBUG: _find_set: searching isw_bjhfihdefe_Storage
DEBUG: _find_set: searching isw_bjhfihdefe_Storage
DEBUG: _find_set: found isw_bjhfihdefe_Storage
DEBUG: _find_set: found isw_bjhfihdefe_Storage
NOTICE: added /dev/sdb to RAID set "isw_bjhfihdefe"
DEBUG: _find_set: searching isw_bjhfihdefe
DEBUG: _find_set: found isw_bjhfihdefe
DEBUG: _find_set: searching isw_bjhfihdefe_Storage
DEBUG: _find_set: searching isw_bjhfihdefe_Storage
DEBUG: _find_set: found isw_bjhfihdefe_Storage
DEBUG: _find_set: found isw_bjhfihdefe_Storage
NOTICE: added /dev/sda to RAID set "isw_bjhfihdefe"
DEBUG: checking isw device "/dev/sda"
DEBUG: checking isw device "/dev/sdb"
DEBUG: checking isw device "/dev/sdc"
DEBUG: set status of set "isw_bjhfihdefe_Storage" to 16
RAID set "isw_bjhfihdefe_Storage" already active
INFO: Activating GROUP raid set "isw_bjhfihdefe"
NOTICE: discovering partitions on "isw_bjhfihdefe_Storage"
NOTICE: /dev/mapper/isw_bjhfihdefe_Storage: dos     discovering
NOTICE: /dev/mapper/isw_bjhfihdefe_Storage: dos metadata discovered
DEBUG: _find_set: searching isw_bjhfihdefe_Storage1
DEBUG: _find_set: not found isw_bjhfihdefe_Storage1
NOTICE: created partitioned RAID set(s) for /dev/mapper/isw_bjhfihdefe_Storage
RAID set "isw_bjhfihdefe_Storage1" already active
INFO: Activating partition raid set "isw_bjhfihdefe_Storage1"
WARN: unlocking /var/lock/dmraid/.lock
DEBUG: freeing devices of RAID set "isw_bjhfihdefe_Storage"
DEBUG: freeing device "isw_bjhfihdefe_Storage", path "/dev/sda"
DEBUG: freeing device "isw_bjhfihdefe_Storage", path "/dev/sdb"
DEBUG: freeing device "isw_bjhfihdefe_Storage", path "/dev/sdc"
DEBUG: freeing devices of RAID set "isw_bjhfihdefe"
DEBUG: freeing device "isw_bjhfihdefe", path "/dev/sda"
DEBUG: freeing device "isw_bjhfihdefe", path "/dev/sdb"
DEBUG: freeing device "isw_bjhfihdefe", path "/dev/sdc"
DEBUG: freeing devices of RAID set "isw_bjhfihdefe_Storage1"
DEBUG: freeing device "isw_bjhfihdefe_Storage1", path "/dev/mapper/isw_bjhfihdefe_Storage"



not really sure why it would work on the live version but not the actual install

---

### Post by biebel on 2009-09-13
Hard to tell from that as both the kernel and the dmraid versions have changed since the live version.

When I was unable to mount my nv_raid with jaunty at all I could still mount it manually with the older version.
```

apt-cache policy dmraid

```
will give you the version in use. (Installed: 1.0.0.rc15-6ubuntu2)

Do that in live environment and hunt down and install the corresponding .deb files in the ubuntu archives.
you'll need dmraid_*version"_*architecture".deb and libdmraid*version*_architecture.deb

If that doesn't help it's probably kernel related and you could revert back to the kernel on the live cd as well.
```

uname -a

```
That will give you the kernel version in use.

Jaunty does seem more bug-ridden than any other ubuntu version before. I would have switched back to 8.10 if it had out of the box ext4 support tbh. On the upside, I have learned more about linux/ubuntu trying to get things working again with jaunty than with any other version too ;)

---


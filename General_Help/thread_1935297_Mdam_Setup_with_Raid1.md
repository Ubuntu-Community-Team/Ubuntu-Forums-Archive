---
title: "Mdam Setup with Raid1"
date: 2012-03-04
forum: General Help
---

### Post by just_cruising on 2012-03-04
Hey when I did my install of ubuntu I didn't configure RAID1. I want to setup my 2x1tb drives in RAID1 with Mdam. Is it possible to do this post installation and if so how?

---

### Post by raja.genupula on 2012-03-04
[http://www.howtoforge.com/software-raid1-grub-boot-debian-etch](http://www.howtoforge.com/software-raid1-grub-boot-debian-etch)

look at that

---

### Post by just_cruising on 2012-03-04
Thanks I'm looking for something where RAID1 isn't with the OS drive. The RAID1 will be for pure data and not the OS.

---

### Post by just_cruising on 2012-03-04
currently have just done a cat /proc/mdstat and got the following

nathan@MediaServer:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid1 sde1[1] sdc1[0]
      976758841 blocks super 1.2 [2/2] [UU]
      [=>...................]  resync =  7.3% (71652800/976758841) finish=190.8min speed=79028K/sec
      
unused devices: <none>

Looks like it is going to take a while to sync the raid array
My next question is what do I format the RAID array as, EXT3 or EXT4?

---

### Post by just_cruising on 2012-03-06
I'm stuck what should i be putting in my mdadm.conf file. This is what I have 

@MediaServer:~$ cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid1 sde1[1] sdc1[0]
976758841 blocks super 1.2 [2/2] [UU]

unused devices: <none>

Mdadm.conf file that I have at the moment

Code:
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays

# This file was auto-generated on Sun, 26 Feb 2012 21:26:43 +1000
# by mkconf $Id$

---

### Post by kmanley57 on 2012-03-06
I formated my 2-1.5 TB drives as ext4 yesterday. It is more which do you feel is more stable to use as a format option. I am lazy though and used the disk utility when I set up my raid yesterday on my local file server. Ext4 is/was the default and I did not change it. It did take a while to resync the drives, but I also was writing files onto it while it was syncing. 8^)

My mdadm.conf file looks just like yours, so I think you just need to mount it where you want the raid to be after you format the Raid partition on it. As you can tell from what I did you can finish setting it up while it is resyncing the two drives. so just format it then mount it.

Well I rebooted and the array still does not work, so back to figuring out what it needs!

---

### Post by kmanley57 on 2012-03-07
Here is what I currently have:

$cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid1 sdc[1] sdb[0]
      1465137424 blocks super 1.2 [2/2] [UU]
      
unused devices: <none>

then in /etc/mdadm/mdam.conf:

# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default (built-in), scan all partitions (/proc/partitions) and all
# containers for MD superblocks. alternatively, specify devices to scan, using
# wildcards if desired.
DEVICE /dev/sdb* /dev/sdc*

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays

# This file was auto-generated on Mon, 05 Mar 2012 14:02:12 -0700
# by mkconf $Id$

ARRAY /dev/md/0 metadata=1.2 UUID=582b0bc2:7a596bd8:2fa0c1bc:df2ebb4a name=Ubuntu-server:0


last line taken from result of command in manual pages for mdadm.conf.
Look in the 'level=" section of ARRAY.

'mdadm --examine --scan'

I am using the 12.04 release of Ubuntu so you may get different results.

---

### Post by just_cruising on 2012-03-09
> **kmanley57 said:**
> Well I rebooted and the array still does not work, so back to figuring out what it needs!

Did you work it out, I have updated my mdadm.conf file and looks like this:

```
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays

# This file was auto-generated on Sun, 26 Feb 2012 21:26:43 +1000
# by mkconf $Id$

ARRAY /dev/md0 level=raid1 num-devices=2 UUID=80d8be84-15c6-4f99-a235-7484afdfeeac
```

I then do the following:

```
nathan@MediaServer:~$ sudo mdadm --examine --scan
ARRAY /dev/md/0 metadata=1.2 UUID=6b45aed5:a6518adf:1a8a8351:83fcf7eb name=MediaServer:0
nathan@MediaServer:~$ sudo mdadm --detail /dev/md0
mdadm: cannot open /dev/md0: No such file or directory
```

Why is it that it comes up file or directory yet I can mount it via Computer but can't write to it?

---

### Post by just_cruising on 2012-03-10
Bump - anyone got some suggestions?

---


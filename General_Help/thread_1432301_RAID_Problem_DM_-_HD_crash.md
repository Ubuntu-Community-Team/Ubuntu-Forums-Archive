---
title: "RAID Problem DM - HD crash"
date: 2010-03-17
forum: General Help
---

### Post by Camicia on 2010-03-17
Hi,
We have 4 HDs on our server. One of them broke last night. I could see a message on the server and after restarting the S.M.A.R.T. on the BIOS was recognising one HD as bad.

After removing the failing HD, the server is now up and running.

I have a problem: **I do not remember how I configured the HDs**. During the installation I had a few problems and I change a few times what I wanted to do.
I am sure I had at least a RAID0 with 2 disks but I could have put all the 4 disk in the RAID having 2 disks as spare drives **or** I may have created another volume for the other 2....

How do I find out what is going on? dmraid return: No raid disks
```
$ sudo dmraid -ay -vvv -d
WARN: locking /var/lock/dmraid/.lock
NOTICE: /dev/sdc: asr     discovering
NOTICE: /dev/sdc: ddf1    discovering
NOTICE: /dev/sdc: hpt37x  discovering
NOTICE: /dev/sdc: hpt45x  discovering
NOTICE: /dev/sdc: isw     discovering
DEBUG: not isw at 500107860992
DEBUG: isw trying hard coded -2115 offset.
DEBUG: not isw at 500106779136
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
DEBUG: not isw at 500107860992
DEBUG: isw trying hard coded -2115 offset.
DEBUG: not isw at 500106779136
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
DEBUG: not isw at 500107860992
DEBUG: isw trying hard coded -2115 offset.
DEBUG: not isw at 500106779136
NOTICE: /dev/sda: jmicron discovering
NOTICE: /dev/sda: lsi     discovering
NOTICE: /dev/sda: nvidia  discovering
NOTICE: /dev/sda: pdc     discovering
NOTICE: /dev/sda: sil     discovering
NOTICE: /dev/sda: via     discovering
no raid disks
WARN: unlocking /var/lock/dmraid/.lock
```MountManager seems to report that sda and sdb belong to linux_raid_member.
However there is no mount point.

Questions:
1-How do I find how the disk were and are configured?
2-How can I find what was on the disk that died? (Was it a spare drive or one of the 2 in mirror)?
3-What do I need to do now to be sure that the mirroring is working OK? (considering that there is a spare drive). Do I need to use a command to let ubuntu mirror the drive on the new one?
4-What do I need to do when I get a replacement of the broken disk? 
5-What is an utility that can show me easily how the disks are configured and eventually makes a change.

Thank you ion advance
-Chris

---

### Post by Camicia on 2010-03-19
up!

---

### Post by Camicia on 2010-03-24
Help!

---

### Post by Camicia on 2010-04-01
New disk is arrived. I connected it. Now what should I do?

---


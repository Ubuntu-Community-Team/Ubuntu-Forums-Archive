---
title: "mdadm: only give one device per ARRAY line: /dev/md/:raid and array"
date: 2012-03-02
forum: General Help
---

### Post by laughingman77 on 2012-03-02
Hi all,

First post here, and I hope I have the correct forum:

I recently fixed redirecting root mail to my account in thunderbird, and  realised I was has receiving daily email reports from anacron  (cron.daily), re mdadm.
```
/etc/cron.daily/mdadm: 
mdadm: only give one device per ARRAY line: */dev/md/*:raid and array 
```I looked up the particular cron job, and tried the command manually, and received the same error message
```
$ sudo mdadm --monitor --scan --oneshot
mdadm: only give one device per ARRAY line: /dev/md/:raid and  array
```I checked out mdadm.conf, but could not see anything  obvious, other than a reference to my old array (presumably from when I  imported the backup after a botched remount after a reinstall), which I  commented out. I tried referring to the device by its /dev path rather  than UUID, but made no difference.
fstab:
```
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=3f458052-e09e-4bc7-a54b-0fb9d7d114c6 none            swap    sw              0       0
#UUID=86dc953d-4ebc-4a6e-a4e5-8fbede80d552    /media/raid    ext4    defaults    0    2
/dev/md127    /media/raid    ext4    defaults    0    2
```mdadm.conf
```
DEVICE partitions
ARRAY /dev/md/:raid metadata=1.2 name=:raid array UUID=f9099a38:9bd89ac8:a955705d:3a3244ad
#ARRAY /dev/md/:raid metadata=1.2 name=:raid array /dev/md127

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
#ARRAY /dev/md/0 metadata=1.0 UUID=25c0930f:743a64e7:69503f88:5de3a7a4  name=linux-ynag:0
```The array contains 4 disks in RAID5, and is  mounted perfectly, and I can access the data with no problem. It worries  me a little, because it may mean that there is something wrong in the  configuration and/or I will not receive any disk fail alerts.

Thanks in advance

---

### Post by laughingman77 on 2012-03-05
hmmm, am I the only one with this error, nobody has an idea?

---

### Post by laughingman77 on 2012-03-09
bump

---


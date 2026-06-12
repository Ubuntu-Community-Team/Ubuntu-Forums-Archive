---
title: "2/14 hdds disappear, give input/output error"
date: 2011-03-22
forum: General Help
---

### Post by shortridge11 on 2011-03-22
I've got 14 drives in a machine running 10.04 and every now and then 2 of the drives just seem to disappear.  If i restart the machine (very undesirable) then they come back. I figured if the drives were actually bad then ubuntu would give me some type of disk warning, like it did when a previous drive went bad.  Is it possible i just have something misconfigured?

---

### Post by shortridge11 on 2011-03-23
df```
xxx@xxx:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdg3              74G  4.9G   65G   7% /
none                 1000M  364K 1000M   1% /dev
none                 1005M  192K 1004M   1% /dev/shm
none                 1005M  524K 1004M   1% /var/run
none                 1005M     0 1005M   0% /var/lock
none                 1005M     0 1005M   0% /lib/init/rw
none                   74G  4.9G   65G   7% /var/lib/ureadahead/debugfs
/dev/sdg5             112G  105G  7.4G  94% /media/x1
/dev/sdg6             1.2T  680G  530G  57% /media/x2
/dev/sdf2             293G  268G   25G  92% /media/x3
/dev/sdf1             782G  499G  283G  64% /media/x4
/dev/sdc1             1.4T  1.1T  355G  75% /media/x5
/dev/sda1             1.9T  1.1T  786G  58% /media/x6
/dev/sdd1             1.4T  1.4T   35G  98% /media/x7
/dev/sdf3             323G  122G  202G  38% /media/x8
/dev/sde1             781G  4.2M  781G   1% /media/x9
/dev/sdb1             196G  101G   95G  52% /media/x10
/dev/sdb2             1.7T  1.2T  528G  69% /media/x11
/dev/sde2             1.1T  4.2M  1.1T   1% /media/x12
xxx@xxx:~$

```

and my fstab
```
xxx@xxx:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system>                             <mount point>    <type> <options>        <dump>  <pass>
proc                                        /proc            proc   nodev,noexec,nosuid  0       0

#Root (DO NOT TOUCH)
UUID=c06df46e-d82b-4345-987d-d69571cb6b6a   /                ext4   errors=remount-ro    0       1

#Swap
UUID=426fcda2-b980-40a9-8337-136dea88bf15 none               swap   sw                   0       0

#Floppy
#/dev/fd0                                   /media/floppy0 auto rw,user,noauto,exec,utf8 0       0

#x1
UUID=a90ef25f-f180-4648-a2be-aaa8aac3c481   /media/x1     xfs    defaults             0       0

#x2
UUID=77d3a47a-1e88-4d03-a128-f6fbea206b6a   /media/x2    xfs    defaults             0       0

#x3
UUID=02d42310-8852-4296-a567-f3e5c995b575   /media/x3 xfs    defaults             0       0

#x4
UUID=b0fac62b-d74f-441e-8437-3495d0a3c41c   /media/x4 xfs    defaults             0       0

#x5
UUID=883f1e01-8115-43c7-8c59-d22543d440a6   /media/x5      xfs    defaults             0       0

#x6
UUID=fbabeccf-bf35-4fac-b4b4-5a35354cd3fe   /media/x6       xfs    defaults             0       0

#x7
UUID=fa4aaa85-5655-4dba-8d11-1efe34221338   /media/x7   xfs    defaults             0       0

#x8
UUID=5611cd7d-cf3a-4dad-8023-fc7670ae466a   /media/x8  xfs    defaults             0       0

#x9
UUID=f50a39a1-798c-4df1-91af-1417ee953ee4   /media/x9  xfs    defaults             0       0

#x10
UUID=08e38e8f-7862-45c9-a6c7-7b6e2c0d75b5   /media/x10     xfs    defaults             0       0

#x11
UUID=7f99d4d8-0b97-4739-b289-dc4ddf5b4bea   /media/x11      xfs    defaults             0       0

#x12
UUID=a6db457b-21f7-48c4-9170-23c273e0ddc6   /media/x12     xfs    defaults             0       0
xxx@xxx:~$

```

note: my gf needed access to 2 of the drives that went down, so i had to restart again. problem is not presenting itself at this moment, i'll probably repost the df when it does.

the 2 drives that go away are x3, x6

---

### Post by shortridge11 on 2011-03-23
Problem has returned, only one drive is not there, df -h yields identical output.  ls /media/xx gives this error```
ls: cannot open directory .: Input/output error

```

---

### Post by shortridge11 on 2011-03-25
well, now 3 drives are offline. I'm confused why this is happening =\

---

### Post by jerome1232 on 2011-03-25
Are you sure your Power Supply has enough beef to power all of those drives? That could be one reason for intermittent failure like that. I would also double check all cabling on the problem disks.

To the problem disks have anything in common (connected to the same power rail maybe?)

---

### Post by shortridge11 on 2011-03-25
power supply could be an issue, i didn't think of that. I'll try a higher watt power supply and let you know

---


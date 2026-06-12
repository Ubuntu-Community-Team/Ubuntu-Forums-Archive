---
title: "hard disks do not spin down"
date: 2010-05-20
forum: General Help
---

### Post by Run Seven on 2010-05-20
Hi,

I have the following problem: 

I have two 1 GB hard disks set up as a RAID-1 array which is working fine. I have set both hard disks to a spindown delay of 2:30 minutes using hdparm (spin down is checked in power management as well).

```
sudo hdparm -S 30 /dev/sda
sudo hdparm -S 30 /dev/sdb

```

The raid array consists of two partitions. It is installed in a small server running from a USB stick (i.e. no swap or other system critical partitions on the harddisks).

Even if I dismount both partitions of the RAID array (which, at least to me, should mean that no writing or reading from the array should take place), I can hear the clicking of the hard disks from time to time and the hard disks refuse to spin down (checked via hdparm -C /dev/sda: harddisk is active/idle).

Any suggestions? Should I stop the RAID array perhaps, too? I would prefer a solution which does not require dismounting the partitions.

Thanks
Run Seven

---

### Post by dino99 on 2010-05-20
You can set spindown time in /etc/hdparm.conf if you uncomment the line with #spindown_time = 24

maybe you need to update rc.d too

---

### Post by Run Seven on 2010-05-20
> **dino99 said:**
> You can set spindown time in /etc/hdparm.conf if you uncomment the line with #spindown_time = 24


Thanks, I did that... unfortunately still no spindown

> maybe you need to update rc.d too

Sorry, I don't know how I would do that... and Google didn't help me much in this matter... what would I need to update rc.d for if hdparm.conf is edited the way you suggested?

Update: Even with the raid array stopped, the hard disks won't spin down. What the hell is Ubuntu doing with my hard disks?

Update 2: if I spin down manually (hdparm -y /dev/sdx), the drives remain spun down. Still, why not automatically?

---

### Post by Run Seven on 2010-05-31
I have spent a few more hours tinkering but still, the hard disks do not spin down. Any suggestions, anyone?

---

### Post by KrisWragg on 2010-06-03
I am suffering from the same problem with my system.

I have two hard drives, one is purely storage, the other has root file system, swap and another storage partition on it.

hdparm -Y will powerdown both drives, although the root file system drive spins back up quite quickly.

hdparm -S will not work, they will occasionally spindown only to come straight back down.

I have set noatime on all partitions which I thought would at least alleviate the problem on the pure storage drive, but nope...

Perhaps a problem with hdparm?

---

### Post by wiz-oz on 2010-06-04
If you're using Lucid, have a look at this:

[https://bugs.launchpad.net/bugs/568120]("https://bugs.launchpad.net/bugs/568120")

cheers,

Oscar

---

### Post by Run Seven on 2010-06-05
Thank you Oscar. Indeed, I run Lucid. Unfortunately, the solution in comment #21 does not work for me. I guess I will have to wait until this problem is fixed. In 9.10, everything worked fine.

---

### Post by bluelamp999 on 2010-06-10
Hello,

Has anyone any more info on this issue?

I've just built a 10.04 home server (Atom D510) with 3 x 1.5TB Samsung 'green' drives in an mdadm RAID5 array.

I'd like them to spin down when inactive for an hour or so using something like...```
/dev/sda {
spindown_time = 242
}
``` in hdparm.conf.

But judging by this thread (and the bug report already mentioned) this won't work...

Is this really the case?

If so, how long before this is addressed?

Cheers

---

### Post by Run Seven on 2010-06-11
It is working for me now with 10.04. I got the solution in the link Oscar provided at last to work. For your convenience, this is what worked for me:

Just install the current ubuntu version of hdparm and add 

```
/dev/sdx {
    apm = 255
    apm_battery = 254
}

```

to your hdparm.conf in /etc (replace /dev/sdx with your drive).

Feel free to replace the values as you wish (e.g. some people might want to use "apm = 254").

---

### Post by cmcginty on 2011-01-02
RunSeven, I just want to clarify:

```
apm_battery
``` is irrelevant for desktop systems.

```
apm = 255
``` disables the APM feature on the disk. I'm guessing the reason for this, is that enabling APM interferes with the spindown value? However disabling APM seems to be counterintuitive.

---

### Post by bobharvey on 2011-04-08
> **cmcginty said:**
> RunSeven, I just want to clarify...However disabling APM seems to be counterintuitive.

and my disks say they do not support APM ( hdparm -B ) and the hdparm.conf on my 10.04 LTS does nothing.  There appear to be two  Bugs open:
[https://bugs.launchpad.net/ubuntu/+source/hdparm/+bug/568120](https://bugs.launchpad.net/ubuntu/+source/hdparm/+bug/568120)
[https://bugs.launchpad.net/ubuntu/+source/hdparm/+bug/595138](https://bugs.launchpad.net/ubuntu/+source/hdparm/+bug/595138)
and nothing happening.
:confused:

---

### Post by mikedoth on 2011-04-10
My setup seems to be working, the setup looks like this (after several weeks of experimenting).

mdadm.conf: ARRAY /dev/md0/ level=mirror num-devices=2 UUID=TooLongToType

fstab: Not using UUIDs (made no diff) > /dev/md0p1 /media/BackupRaid ext4 rw,user,auto,exec 0 0

HDParm: /dev/sdd { spindown_time = 242 } Must be pointed to each drive in the array, not the md0...

Smart Tools: /etc/smartd.conf and add “-n standby,q” to the DEVICESCAN line or it will never spin down because it's constantly being accessed.

---

### Post by arryo on 2012-05-03
I tried all of the suggestions but it seems my 3 harddrives on raid 5 won't go standby

Even when i used the command 

```

hdparm -y /dev/sda /dev/sdc /dev/sdd

```

and check with 

```
hdparm -C /dev/sda
```

the result is still active/idle

I have fresh new ubuntu server 12.04 on USB with nothing it it yet except SSH, mdadm, smartmontools, and hdparm

---

### Post by oldos2er on 2012-05-03
Old thread closed. Please start a new thread for your question or problem.

---


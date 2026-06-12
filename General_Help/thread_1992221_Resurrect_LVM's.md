---
title: "Resurrect LVM's"
date: 2012-05-31
forum: General Help
---

### Post by flycast on 2012-05-31
I have been running Zentyal server but have been generally unhappy with the lack of help in the forums. I want to make the switch to Ubuntu. Tons of users and a real helpful user base.

I have two sets of disks. The first set has my current OS and is a 150 Gb raid1. The current system won't boot because it cannot find the sbin/init folder from a failed install of CrashPlanPro (funny, I know).

I have a couple of 2 Tb drives in a raid1 for data drives and those drives are partitioned using LVM. Both sets of raids are controlled by an LSI chip on the motherboard.

I am currently downloading an iso for desktop Ubuntu so I can try to fix my boot disk but have little hope for that.

I want to:
1) See my data on the LVM's either by fixing the current Zentyal/Ubuntu OS, using the desktop boot disk or installing Ubuntu server and then Webmin.

2) After I see my data safe and sound I want to unplug my data drives and install Ubuntu server, a GUI and Webmin.

The main question...how do I get my LVM configuration if I cannot fix my current Zentyal/Ubuntu OS using fsck?

---

### Post by irv on 2012-05-31
Why don't you try GParted LiveCD you can download it from DistroWatch.
[http://distrowatch.com/table.php?distribution=gparted]("http://distrowatch.com/table.php?distribution=gparted")
Burn a CD and boot with this and fix your drive.

---

### Post by flycast on 2012-05-31
OK. I ran gparted, I can see the partitions. I performed a check and repair on the boot disk and no luck. Same error.

---

### Post by steeldriver on 2012-05-31
Isn't the bigger issue likely to be that the LVM is on top of RAID? Is it true H/W raid / fakeraid / Linux? I would think that pretty much any modern Live distribution will be able to see / manipulate LVM volumes once the array is assembled.

FWIW I don't think regular block device tools like parted / gparted will be able to help you much here - when I look at the LVM disks on my system with parted it can see the basic partition structure but doesn't report any type information (no 'linux-lvm' or whatever). I have to use the LVM2 tools (pvdisplay / lvdisplay) to see the volumes.

But until the underlying raid is assembled I don't see you getting very far.

---

### Post by flycast on 2012-05-31
I think what I will do is the following:
1) Physically unplug the two raid 2Tb drives.
2) Perform a fresh install of Ubuntu server 12.04, GUI and Webmin on the boot drive.
3) Reconnect the two 2Tb drives.
4) Set up the LVM to "see" my data on the 2Tb drives I just reconnected.
5) Set up file sharing on the data (not a big deal since only a few were actually connecting to the data).

Sound reasonable?

---


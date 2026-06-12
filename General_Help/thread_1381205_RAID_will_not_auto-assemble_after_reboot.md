---
title: "RAID will not auto-assemble after reboot"
date: 2010-01-14
forum: General Help
---

### Post by erythros on 2010-01-14
I had an 8 disk RAID 5 running under Slackware. I decided to switch to the newest Xubuntu. My OS is loaded to a 9th hard drive so that I can swap out this drive without affecting the RAID.
 
After the CD install, necessary updates, and required applications install I rebooted, and looked for my array. mdadm.conf file showed two UUIDs, both with the same specs as my RAID.** mdadm -D --scan** did not show any assembled arrays.** mdadm --assemble --scan** assembles my array without issue and I can mount the array and verify my data is intact.
 
However upon reboot the there is no assembled array. I used different options while assembling the array, updating the UUID, resyncing the array... Each reboot ended with the array having to be assembled manually. Another review of the mdadm.conf leads me to believe it is the double line. After verifying the UUID on the assmbled array via **mdadm -D --scan** I deleted the line that had the mismatching UUID.
 
The problem persisted. The RAID would not auto assemble after reboot. I gave up for a short time and merely added the commands to assemble the array and mount it in rc.local.
 
It was till tonight that I solved it. While attacking the problem again I noticed that **mdadm -E --scan -v** shows the two arrays. The devices of one were listed as /dev/sda, /dev/sdb, /dev/sdc, etc... while the devices of the second were listed as /dev/sda1, /dev/sdb1, /dev/sdc1, etc... So there are valid superblocks for the drives, as well as the partitions. I reviewed mdadm.conf again because I remembered reading something about scanning for devices. Sure enough the first keyword **DEVICE** is set to **partitions**. **cat /proc/partitions** displays sda, sda1, sdb, sdb1, sdc, sdc1, etc... I assume that therein lies the problem. There is correct, but different, superblock info for each drive versus each drives partition. Not knowing how to fix the dual superblock issue I decided to see if editing mdadm.conf to explicitly see only the partitions I chose would end this mdadm confusion: **DEVICE /dev/sd[abcdefgh]1**
 
**mdadm -D --scan** now shows an assembled array after reboot. I edited fstab to auto-mount the array and now after a few reboot test the array is always present.
 
 
So as a recap:
 
mdadm would not auto-assemble array on reboot.
manual assmble works.
mdadm saw two arrays (each with a unique UUID) when there was actually only one (physically).
editied mdadm.conf to load the specific devices (partitions in this case)
mdadm now auto-assembles array on reboot
 
 
If anyone knows why there is superblock information for the entire drive as well as the partitions, or how to correct that without losing data on the array I'd like to know.

---


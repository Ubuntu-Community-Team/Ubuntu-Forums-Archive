---
title: "one of my spares is missing...or is it?"
date: 2010-05-10
forum: General Help
---

### Post by davidmaxwaterman on 2010-05-10
I have a 6+2 disk RAID5 array. If I do mdadm --detail, it shows me 6 active, working 8, failed 0 and spare 2, as expected. However, in Disk Utility, it tells me I have two arrays, the one I expect, but with 6+1; and another with no disks. When I look through my disks, I see there's one which is 'different'. While I had made all my 8 disks partition-less, this one seems to have developed a partition somehow - "Linux RAID autodetect". Also, when I click on 'Go to array', it takes me to this other odd diskless array.

How can I get my disks to behave themselves?

(Also, I think these disks seem to move around devices for some reason).

Max.

---

### Post by kidders on 2010-05-11
Hi there,

That doesn't seem like anything to worry about, imo. I suspect that if you remove the misbehaving spare from your array, erase the first few megabytes of it & re-add it, the disk utility might stop reporting the phantom array.

My guess is the data on one of your spares looks to the disk utility like a RAID superblock, either out of pure coincidence, or because it used to be part of an old array. Erasing that data should solve the problem. Then again, you *could* just ignore it.

Every now and then, I find MacOS mistakes my Linux swap partitions for FAT filesystems, presumably because certain key bytes near the start of the partitions just happen to contain the right values. Something similar may be happening on your Ubuntu box. As long as mdadm is happy, what the disk utility thinks it sees doesn't really matter.

I hope that helps.



In general, I'd recommend always erasing the start of any device you add to a RAID array. If your current array ever became degraded or damaged, spurious metadata from a disk's previous life could create confusion.

---

### Post by davidmaxwaterman on 2010-05-12
> **kidders said:**
> 
I hope that helps.


Yeah. I think I had tried this erasing/formating trick before, but it still mis-behaved; but it seems to be now, so I guess I did it differently this time, somehow...

I wonder why Disk Utility is saying 'SMART Status: Unknown' for some of my disks, while for others it is saying 'Disk is healthy'. Any ideas about that?

Actually, all the disks in the array proper are 'Unknown'; only the other spare is 'healthy', as well as the disks which aren't part of the array.

Is this something related to using the disks as raw devices rather than partitioning them and making the partitions part of the array? I suppose I can try erasing the other spare to see if it becomes 'Unknown' too, though I really would prefer all the disks to become 'healthy'...I did run all the extended self-test on all of them, but it didn't seem to make any difference.

Max.

---

### Post by kidders on 2010-05-12
Hey again,

> **davidmaxwaterman said:**
> I suppose I can try erasing the other spare to see if it becomes  'Unknown' tooSMART doesn't have anything to do with what's stored on a disk, so that wouldn't make any difference. "Unknown" just means that the hardware and/or its interface don't support it.

Assuming all your disks support SMART (which they may not), the problem is most likely the way they're connected to your motherboard, or the way the disk utility is querying them. There may not be much you can do.

Try using smartctl to query your disks directly (ie cut the disk utility out of the picture).

---

### Post by davidmaxwaterman on 2010-05-13
> **kidders said:**
> Hey again,

SMART doesn't have anything to do with what's stored on a disk, so that wouldn't make any difference.


Well, yeah, though I thought perhaps that the act of writing to the entire disk might result in it being known to be good.

> "Unknown" just means that the hardware and/or its interface don't support it.


Well, all the disks are identical (as is common for a RAID), so I expect they do support it. In fact, when I click on the 'SMART Data' button, it shows me all sort of stuff...mostly the 'Assessment' is "Good", but :

"Power-On Hours"
"Power Cycle Count"
"Temperature"
"Reallocation Count"
"Current Pending Sector Count"
"Uncorrectable Sector Count" and
"UDMA CRC Error Rate"

are all marked "N/A". Having said that, those are "N/A" for the 'healthy' disk too - in fact, the healthy disk has an additional "N/A" for "Start/Stop Count".

The 'Unknown' seems to come from the 'Self Assessment: Unknown' part, so I'll try running another self-test and keep the system up until the 'Self-tests' progress is done.

...shrug...

I guess I'm a little worried because all the disks are quite old now - power on time is 2.5 years for this disk I'm running a self-test on right now.

I notice this :

sudo mdadm --detail /dev/md2 | awk '/\/dev\/sd/ { print $NF }' | xargs -n1 sudo smartctl -H | grep result
SMART overall-health self-assessment test result: PASSED
SMART overall-health self-assessment test result: PASSED
SMART overall-health self-assessment test result: PASSED
SMART overall-health self-assessment test result: PASSED
SMART overall-health self-assessment test result: PASSED
SMART overall-health self-assessment test result: PASSED
SMART overall-health self-assessment test result: PASSED
SMART overall-health self-assessment test result: PASSED

Which makes me think this is just a bug in the Disk Utility.

> 
Try using smartctl to query your disks directly (ie cut the disk utility out of the picture).

Indeed...looks suspiciously like Disk Utility doesn't work correctly...perhaps I'll take a look at the code.

What do you think?

Max.

---

### Post by kidders on 2010-05-13
Yip... you might be right!

---


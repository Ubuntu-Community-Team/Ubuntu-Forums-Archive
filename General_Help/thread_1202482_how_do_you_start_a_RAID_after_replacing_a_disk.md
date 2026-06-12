---
title: "how do you start a RAID after replacing a disk?"
date: 2009-07-02
forum: General Help
---

### Post by Locke2053 on 2009-07-02
I have a RAID-5 in which one drive failed. I replaced the drive with another, which added as a spare. I assembled the array, but it won't start because it is degraded due to the failed disk being gone.

What command to I need to issue to start my array in degraded mode? mdadm will assemble my array just fine, but won't start it because it is degraded. I've tried madam --run /dev/md0, but that gives an I/O error, so I assume that's the wrong command to use...

---

### Post by Boondoklife on 2009-07-02
Give this site a go [http://www.linuxquestions.org/questions/linux-server-73/mdadm-raid-5-single-drive-failure-644325/](http://www.linuxquestions.org/questions/linux-server-73/mdadm-raid-5-single-drive-failure-644325/)

---

### Post by Locke2053 on 2009-07-02
Thanks for the suggestion. This part: "sfdisk -d /dev/sda | sfdisk /dev/sdd" terrifies me, though. It is definitely a hack, so I'm only going to try that if every other option fails. Has anyone here successfully recovered from a disk failure? What commands did you use?

---

### Post by hibliss on 2009-07-02
Here is a previous post with a similar issue -- [http://ubuntuforums.org/showpost.php?p=7387446&postcount=4]("http://ubuntuforums.org/showpost.php?p=7387446&postcount=4")

---

### Post by Locke2053 on 2009-07-02
Thanks, hbliss. What you linked suggests doing this:

> mdadm /dev/md0 -r /dev/sd?? (remove the failed drive)
Pull the drive, add in a replacement. Partition it if your array is on partitions, then:
mdadm /dev/md0 -a /dev/sd?? (add the new drive)

I have physically removed the failed drive. Therefore, this drive has no /dev/sd?? reference, meaning I can't execute "-r". 

I *did* execute "-a" to add the new drive. When I query my /dev/md0 right now, it lists my good drives (as "synced" or some-such), and it also lists my old drive as being "removed", followed by my new drive, as "spare".

mdadm will assemble, but not start, the array. Even with the dead disk marked as "removed" and a new disk in there as "spare."

---

### Post by Boondoklife on 2009-07-02
> **Locke2053 said:**
> Thanks for the suggestion. This part: "sfdisk -d /dev/sda | sfdisk /dev/sdd" terrifies me, though. It is definitely a hack, so I'm only going to try that if every other option fails. Has anyone here successfully recovered from a disk failure? What commands did you use?

Well all that is doing is ensureing the partition tables are the same, it copies it from sda (a drive that is in the array) to sdd (the new drive). Not really a hack, just making sure the size is the same, you could di it by hand with fdisk but why?

---

### Post by Boondoklife on 2009-07-02
Can you post the output of cat /proc/mdstat

---

### Post by Locke2053 on 2009-07-02
I think I found the problem, but I don't know how to fix it.
```

# mdadm --examine /dev/sdc1 | grep this
this     3       8       49        3      active sync   /dev/sdd1
# mdadm --examine /dev/sdd1 | grep this
this     0       8        1        0      active sync   /dev/sda1

```

My superblocks seem to disagree with my OS as to what drive letter they are. How can I tell mdadm to "ignore the letters, just start based on the UUID"?

---


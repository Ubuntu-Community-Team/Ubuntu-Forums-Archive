---
title: "expand windows partition in dual boot"
date: 2010-04-14
forum: General Help
---

### Post by nafihsus on 2010-04-14
:confused:  I ran out of space in my windows partition and don't know how to move the freed up partition (among my 9.1 partitions) behind the windows boot partition so I can expand it. 

The attached image shows my gparted screenshot. Id like to merge sda2 with sda8 (which was part of my /home partition before and formatted to ntfs in the meantime). 

Help is highly appreciated.

Regards, Cenk

---

### Post by drs305 on 2010-04-14
This will take some time. It can be done but will require multiple steps since sda8 is inside the extended partition.

If sda8 is empty or you don't need the data inside it:
Backup any data that you can't afford to lose.
Defrag sda2 (Windows) from inside Windows. 
Use the Ubuntu LiveCD since you will need to have Ubuntu partitions unmounted.
Delete sda8. (Higher number partitions will need to be unmounted, including swap).
Move Ubuntu (sda5) to the far right.
Shrink the extended partition (sda4) to the right so the unallocated space is outside the extended partition.
Expand sda2 from within Windows.

All this is going to take time. An alternative solution, depending on how much you have specialized Ubuntu, would be to remove everything in the extended partition, expand Windows and then recreate the extended partition and reinstall Ubuntu. Time-wise it may be shorter, but you will lose any changes you have made to Ubuntu.

---

### Post by 98cwitr on 2010-04-14
wouldnt running partition magic in windows be an easier solution?

---

### Post by srs5694 on 2010-04-14
Another option would be to leave the partitions as-is and move some files from the Windows C: drive to /dev/sda8 (D: or E: or whatever it's called in Windows). In fact, this is what I'd recommend. If you use /dev/sda8 for user data files, you'll be able to mount it in Linux to access those files without risking damage to your main Windows installation on /dev/sda2. If you juggle partitions to expand /dev/sda2, OTOH, you'll be risking the whole Windows installation whenever you want to access user data files from Linux. The risk is admittedly small, but why take any risk when you don't have to?

---

### Post by Mark Phelps on 2010-04-14
Having done similar things, I can attest that, regardless of which partitioning tool you use, you will need to do ALL the things that drs305 lists.  

There's no shortcut that will accomplish what you need.

Realize that your screenshot provides no indication of how much free space is available in the NTFS partitions, so there's no way we can tell if you have enough "slack" in your drive to move things around instead of backing them off to an external drive and reloading them.

---

### Post by nafihsus on 2010-04-15
Thx for the comments. sda8 is the part I freed up from my ubuntu home partition. No data on it yet. I don't feel comfortable using 2 partitions for Windows (vista), which I run with almost no software installed other than when I bought the system. But I plan to use windows for photo editing (don't get along with Gimp) and would have no data but only applications to move (re-install).

Done all steps recommended by dsr305 but can't shrink sda4 (all options grey). Maybe it is because sda5-7 are embedded in sda4.

See attachment how Gparted looks now.

---

### Post by drs305 on 2010-04-15
The swap partition is still mounted (sda6). Highlight that partition, then select Partition, Swapoff to unmount it. At that point, sda4 may unmount itself. If not, repeat the procedure for sda4. Then try resizing sda4.

Note: Any partition that is mounted will have a "key" icon next to the name.

---

### Post by nafihsus on 2010-04-15
:) Perfect based on your explanation. Thx a lot.
Here is the final view in gparted.

---


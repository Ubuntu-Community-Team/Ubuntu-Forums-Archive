---
title: "External Hard Drive unable to read after Ubuntu install"
date: 2012-09-24
forum: General Help
---

### Post by Instinct408 on 2012-09-24
Hello, I am a new ubuntu user. I installed ubuntu OS dual boot with windows 7 for school and my external hard drive which I have connected all the time stops working. When I open My computer in windows 7, I see the local disk that corresponds to my external drive (name changed from MyBook to local disk:F). When I try to open the local disk, My Computer just freezes up and nothing happens.

When I try to access the external HD from ubuntu, it said something about not being able to mount. Please help! There are alot of files on my external that I need to access. I have no idea what happened.

During ubuntu installation, it asks if I wanted to partition my External HD on a scroll down list (only option it gave me). I wanted to partition my main HD so I clicked back and disconnected the external HD hoping the scroll down list would chance to my main HD. I then went ahead and clicked next and saw my main HD and started the partition process. Everything seemed to work except my External HD.

Please help me out, and thank you! :D

---

### Post by kurt18947 on 2012-09-25
Do you know how your external HD is formatted?  NTFS?  Can you mount other external devices such as flash drives?  There is one Microsoft file format that linux won't mount without a bit of work (exFAT) but I don't know that there are any shipping devices using that.

---

### Post by Instinct408 on 2012-09-25
> **kurt18947 said:**
> Do you know how your external HD is formatted?  NTFS?  Can you mount other external devices such as flash drives?  There is one Microsoft file format that linux won't mount without a bit of work (exFAT) but I don't know that there are any shipping devices using that.

Im pretty sure its NTFS. For some reason, the hard drive can mount in ubuntu but same problem occurs in windows 7.

---

### Post by Mark Phelps on 2012-09-26
> **Instinct408 said:**
> Im pretty sure its NTFS. For some reason, the hard drive can mount in ubuntu but same problem occurs in windows 7.

You need to try the following using Win7:
1) connect the hard drive
2) open the Disk Management utility, scroll down through the list of "drives" and see if the hard drive is shown in the list
3) if it is shown, it probably does not have a drive letter allocated
4) see if you can assign it a drive letter.

If that works, you will then see the drive's partition in your list of "drives" (MS calls partitions "drives").

If you can't assign a drive letter, that means that the NTFS filesystem is corrupted and you would have to run CHKDSK on it.

---

### Post by Instinct408 on 2012-09-26
> **Mark Phelps said:**
> You need to try the following using Win7:
1) connect the hard drive
2) open the Disk Management utility, scroll down through the list of "drives" and see if the hard drive is shown in the list
3) if it is shown, it probably does not have a drive letter allocated
4) see if you can assign it a drive letter.

If that works, you will then see the drive's partition in your list of "drives" (MS calls partitions "drives").

If you can't assign a drive letter, that means that the NTFS filesystem is corrupted and you would have to run CHKDSK on it.

I did this and my Disk Management utility just froze up along with my chrome. Is my hard drive corrupted? It works when I mount it in Ubuntu.

---

### Post by Rexilion on 2012-09-27
That's weird, try this:

- Boot Ubuntu
- Unplug device
- sudo fdisk -l
- Plug device
- sudo fdisk -l
- You should see a new disk with partitions
- On each of these partitions do:
[code]sudo ntfsfix /dev/<partitionofusb>
- sudo sync
- unplug USB
- shutdown
- plug USB
- boot Windows
- cross your fingers, I hope Windows performs a chdisk on the USB
- try mounting it under Windows

Ntfsfix is part of the ntfs3g suite. It's description (man ntfsfix) mentions this:

> DESCRIPTION
       ntfsfix is a utility that fixes some common NTFS problems.  ntfsfix is NOT a Linux version
       of chkdsk.  It only repairs some fundamental NTFS inconsistencies, resets the NTFS journal
       file and schedules an NTFS consistency check for the first boot into Windows.

       You may run ntfsfix on an NTFS volume if you think it was damaged by Windows or some other
       way and it cannot be mounted.


---

### Post by Instinct408 on 2012-09-29
> **Rexilion said:**
> That's weird, try this:

- Boot Ubuntu
- Unplug device
- sudo fdisk -l
- Plug device
- sudo fdisk -l
- You should see a new disk with partitions
- On each of these partitions do:
[code]sudo ntfsfix /dev/<partitionofusb>
- sudo sync
- unplug USB
- shutdown
- plug USB
- boot Windows
- cross your fingers, I hope Windows performs a chdisk on the USB
- try mounting it under Windows

Ntfsfix is part of the ntfs3g suite. It's description (man ntfsfix) mentions this:

I got to here 

sudo ntfsfix /dev/<partitionofusb>

And it says, Refusing to operate on read-write mounted device /dev/sdc1

What does this mean?

---

### Post by stepking2 on 2012-09-29
By hearing your symptoms, it looks like your drive is about to fail.

---

### Post by Instinct408 on 2012-09-29
> **stepking2 said:**
> By hearing your symptoms, it looks like your drive is about to fail.

My drive was working fine before I installed unbuntu, as a matter of fact, it still mounts correctly in Unbuntu. I am only having problems with windows.

---

### Post by Rexilion on 2012-09-30
> **Instinct408 said:**
> I got to here 

sudo ntfsfix /dev/<partitionofusb>

And it says, Refusing to operate on read-write mounted device /dev/sdc1

What does this mean?

It's a safeguard against modifying a filesystem while it is mounted. If you do that, you are screwed for sure. Think about it: The kernel assume's it's the only one who has direct access so it won't check all the time if everything is still in the same way it's 'supposed' or assumed to be. Now if you start modifying stuff around it's back, bad things happen!

Quick and simple fix for this:

```
umount /dev/sdc1
```

And now try the ntfsfix command again.

P.S. I never said you should mount the system (this can happen automatically though! (by udev, udisks, hal...)).

---


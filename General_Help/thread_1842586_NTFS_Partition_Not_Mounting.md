---
title: "NTFS Partition Not Mounting"
date: 2011-09-11
forum: General Help
---

### Post by cghearn on 2011-09-11
Forgive me if this should be obvious, but I'm not super handy with terminal and I'm trying to recover files from a friends computer. I'm using a recent distro live disc if makes any difference. Below is the error I'm getting. Feel free to direct me to an already answered post if appropriate. Thank you in advance for you time. :)

"Error mounting: mount exited with exit code 13: ntfs_mst_post_read_fixup: magic: 0x05033394  size: 4096  usa_ofs: 16339  usa_count: 43519: Invalid argument
Actual VCN (0xffee02ece66f2f33) of index buffer is different from expected VCN (0x1).
Failed to mount '/dev/sda2': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details."

---

### Post by cghearn on 2011-09-11
--Moved from previous post--

--I tried to run NTFSFIX to give you some context.--

I tried this, but I'm still getting an error that says

"
Mounting volume... FAILED
Attempting to correct errors... 
Processing $MFT and $MFTMirr...
Reading $MFT... OK
Reading $MFTMirr... OK
Comparing $MFTMirr to $MFT... OK
Processing of $MFT and $MFTMirr completed successfully.
Setting required flags on partition... OK
Going to empty the journal ($LogFile)... OK
Remount failed: Input/output error.
"

Any ideas?

---

### Post by Mark Phelps on 2011-09-12
This generally means that the NTFS file system is considered as "dirty" -- and that has to be reset before Linux utilities can use it.

This is most generally done by connecting the drive to an MS Windows PC and running CHKDSK on it.

Some folks will probably tell you that you can "force" the mount of a dirty NTFS partition, and while that it true, you're almost certainly THEN going to get filesystem corruption as a result.

So, you will need to connect this to an MS Windows PC.

---

### Post by Enigmapond on 2011-09-12
I agree I would get to the command-line in windows and run:

```
CHKDSK /r
```

At least this would be the place to start.

---

### Post by coffeecat on 2011-09-12
@cghearn, I've moved the post you made in another thread into this one and it now appears as #2 in this one. It looks as though you tried to run ntfsfix. Mark Phelps and Enigmapond were not aware of this post when they posted. Perhaps you could clarify what you did.

---

### Post by cghearn on 2011-09-18
Ok, so I connected it to a Windows PC and ran chkdsk to no avail. Windows is saying that there is no issue. Any ideas on what the next step would be?

---

### Post by cghearn on 2011-09-18
In case it may help in any way, here is what I see when I view the drive. [IMG]http://cghearn.com/files/Screenshot.png[/IMG]

---

### Post by cghearn on 2011-09-19
:BUMP:

Any chance I can get some help with this? The friend I'm trying to fix this for has no backups of her childrens photos, legal papers, etc. I would appreciate any help available.

---

### Post by Mark Phelps on 2011-09-20
> **cghearn said:**
> :BUMP:

Any chance I can get some help with this? The friend I'm trying to fix this for has no backups of her childrens photos, legal papers, etc. I would appreciate any help available.

Unless I misunderstand what you wrote, you can access this partition Fine using MS Windows, right?

That being the case, then access it via MS Windows and copy the important files off to a USB stick or to an external drive.  Then, connect up the USB or external drive and confirm you can open the files you saved.

If you keep messing around with this in Linux BEFORE you save off these files, you're running the risk of losing them for good!

---

### Post by cghearn on 2011-09-21
> **Mark Phelps said:**
> Unless I misunderstand what you wrote, you can access this partition Fine using MS Windows, right?

That being the case, then access it via MS Windows and copy the important files off to a USB stick or to an external drive.  Then, connect up the USB or external drive and confirm you can open the files you saved.

If you keep messing around with this in Linux BEFORE you save off these files, you're running the risk of losing them for good!

I can access the drive, but all there are, are some folders with a string of numbers, no OS files.

---

### Post by Mark Phelps on 2011-09-22
OK, then if the partition is still formatted NTFS, and you still want to recover the data, suggest you do the following (based on my experience at doing this successfully):
1) Find someone with a working Windows PC
2) Remove your drive from this PC.
3) On the Windows PC, download and install the trial version of GetDataBack for NTFS from Runtime Software.
4) Connect your old drive to this Windows PC.
5) Run GetDataBack in deepest discovery mode -- probably best to let it run overnight.
6) In the morning, check the recovery logs and see if GetDataBack was able to find your lost files.
7) If it was, you will have to purchase it to do the actual recovery. You won't have to reinstall it; instead, they will email you an activation code which you can use to turn on the recovery feature.

And, BTW, it is not HUNDREDS of dollars for this product. Last time I checked, GetDataBack for NTFS was $80, USD.

Your data ... your money ... your choice.

---


---
title: "Restoring NTFS partition"
date: 2010-09-11
forum: General Help
---

### Post by viniciuscarvalho on 2010-09-11
Hi there! I have an external 2TB NTFS drive that I used for my HTPC based on XBMC.

I ran into some problems few months ago, and after searching this forum I found how to fix them by using ntfsfix.

Well everything was working fine (besides the NTFS disk being recognized only on linux :P)

Today I plugged the disk and neither linux or windows can read the disk. It states that there's no partition there.

I have over 600GB of pictures, movies and music, actually everything that I have.

Could someone please point me to some good tools to try to restore that data?

Regards

---

### Post by 300Z on 2010-09-11
Bump. I got the exact same problem here. :(

---

### Post by oldfred on 2010-09-11
ntfsfix only fixes minor things and then sets the NTFS flag to run chkdsk. You should run chkdsk from a windows install or CD.

Run chkdsk several times, until no more errors are detected.
Vista/7 CHKDSK
chkdsk C: /f /r
/f : Fixes errors on the disk.
/r : Locates bad sectors and recovers readable information.
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

If Microsoft's Checkdisk (chkdsk) failed to repair the MFT, run TestDisk, also rebuild boot sector
[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)


If partition need more repair:
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)
Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

---

### Post by viniciuscarvalho on 2010-09-12
Tks OldFred, the only problem is that windows can not mount the volume, so, I can't run chkdsk since I do not have an assigned letter to my partition.

I'm trying some data recovery tools Doctor Data Recovery for NTFS but so far no luck at all :(

---

### Post by Lukas666 on 2010-09-12
> **viniciuscarvalho said:**
> Hi there! I have an external 2TB NTFS drive that I used for my HTPC based on XBMC.

I ran into some problems few months ago, and after searching this forum I found how to fix them by using ntfsfix.

Well everything was working fine (besides the NTFS disk being recognized only on linux :P)

Today I plugged the disk and neither linux or windows can read the disk. It states that there's no partition there.

I have over 600GB of pictures, movies and music, actually everything that I have.

Could someone please point me to some good tools to try to restore that data?

Regards

NEVER use Linux to fix your ntfs problems!

In Windows, the partition may not be mounted, but is it present in the "disk management" section? Here is how to get there:

[http://www.microsoft.com/windowsxp/using/setup/tips/advanced/ntfs.mspx](http://www.microsoft.com/windowsxp/using/setup/tips/advanced/ntfs.mspx)

---

### Post by viniciuscarvalho on 2010-09-12
Well, the windows disk mgmt. Is only useful to format the partition, but that is not a choice for me, I really need to restore the data.

I'm gonna try everything, I really can't loose those data.

Regards

---

### Post by Lukas666 on 2010-09-12
> **viniciuscarvalho said:**
> Well, the windows disk mgmt. Is only useful to format the partition, but that is not a choice for me, I really need to restore the data.

I'm gonna try everything, I really can't loose those data.

Regards

I asked if you could see it there.

---

### Post by Mark Phelps on 2010-09-12
> **viniciuscarvalho said:**
> I'm gonna try everything, I really can't loose those data.

OK, then go to the Runtime Software website and check out the free download of GetDataBack for NTFS.  It's the best NTFS data recovery tool I've ever seen.  You can run the free version to see what it finds and what your chances would be of recoverying the data.

You have to purchase it to do the actual data recovery.

Your data ... your money ... your choice.

---

### Post by viniciuscarvalho on 2010-10-04
Hi there! After two weeks trying, I still had no success on this. I tried most tools, the latest I tried is the testdisk. After over 10 hours analyzing the disk it could not find the partion.

I'm starting to belive that I'll lost all my pictures (which is concerning me most, not caring about the video anymore).

Now, is there any other way to try to recover this data?

Regards

---

### Post by warfacegod on 2010-10-04
Bring it to a specialist. In fact, get estimates from several. From reading this, it looks like you may have seriously jumped the gun by going straight to file recovery instead investigating all options first. I suspect you've probably done more harm than good with the recovery software as well as the initial fix you did with ntfsfix. I think the safest thing you can do at this point it to immediately stop doing anything with it. Do not turn it on. Bring it to an HDD recovery specialist. Pray...if that's your thing.

---

### Post by Mark Phelps on 2010-10-05
> **viniciuscarvalho said:**
> Hi there! After two weeks trying, I still had no success on this. I tried most tools, the latest I tried is the testdisk.

Did you try GetDataBack ... as I suggested?

It's going to cost you a LOT more if you take it to a data recovery service than the $80 or so that Runtime Software wants.  IF you don't try it, you won't know if it works, now will you?

---


---
title: "NTFS Drives vanished"
date: 2012-08-10
forum: General Help
---

### Post by danbrownlow on 2012-08-10
Hey there,

This morning when my friend went to start their computer, it took a lot longer than usual. Once Ubuntu had fired up, there were a lot of messages about (something along the lines of, "System program problem detected", with the options to report the problem or cancel.

When she went to view her NTFS partitions, they'd complete vanished and Ubuntu wouldn't even see them.

We tried using recovery console to run fsck, which came up with a lot of errors. Then I tried using Gparted, which eventually showed all the partitions, but when I tried to repair and check through Gparted, it said the operation had completed successfully but that didn't seem to help either. After that, I tried running fdisk -l which didn't show anything, except coming up with the "Bus error" message.

I'm beginning to think that the drive is possibly dead, but is there anything we can use to try and mount the partition and try and get some data off it?

Thanks.

---

### Post by oldfred on 2012-08-10
If they are NTFS have you run chkdsk from Windows?

Ubuntu will not mount a NTFS partition if it is flagged as needing chkdsk to prevent further damage that chkdsk may not be able to fix.

You can check hard drive by using Disk Utility, click on drive and look at Smart Data. All I know is green is good, but it can run tests and report lots of data.

If you cannot mount NTFS partition you may be able to see data with testdisk or photorec which is part of testdisk.

---

### Post by danbrownlow on 2012-08-10
> **oldfred said:**
> If they are NTFS have you run chkdsk from Windows?

Ubuntu will not mount a NTFS partition if it is flagged as needing chkdsk to prevent further damage that chkdsk may not be able to fix.

You can check hard drive by using Disk Utility, click on drive and look at Smart Data. All I know is green is good, but it can run tests and report lots of data.

If you cannot mount NTFS partition you may be able to see data with testdisk or photorec which is part of testdisk.

At the moment, we have no access to Windows. The NTFS partition was just what remained as it had all her data on, and Ubuntu on a separate partition. 

I've tried to run a few programs, and all I get is a random Bus Error message. Is there anyway I can run a chkdsk from within Ubuntu? Or from a live CD? Disk Utility is refusing to run on the system.

Thanks.

---

### Post by Mark Phelps on 2012-08-10
Unfortunately, when a drive starts to fail, reading sectors takes a very long time.  IF that is your case, since Ubuntu won't mount the NTFS partition, your only recourse to recover that data will be to attach that drive to a Windows PC and use a Windows utility to recover the data to some other drive.

If you're interested in doing that, read on ...

Since your data was on a Windows partition, based on my experience at doing this successfully, my suggestions are the following:
[NOTE: If your PC has a working copy of MS Windows on it, skip to step 4]
1) Find someone with a working MS Windows PC
2) Remove your drive from this PC.
3) Connect your old drive to the MS Windows PC.
4) Download and install the trial version of GetDataBack for NTFS from Runtime Software in MS Windows.
5) Run GetDataBack and select the option to find Deleted files.
6) When done, browse the filesystem in the app to see if your directories and files were found.  If so, view some to confirm the contents are intact.
7) If they are, you will have to purchase GetDataBack to do the actual recovery. You won't have to reinstall it; instead, they will email you an activation code which you can use to turn on the recovery feature.

And, last time I checked, GetDataBack for NTFS was $80, USD.

Your data ... your money ... your choice.

---

### Post by danbrownlow on 2012-08-10
> **Mark Phelps said:**
> Unfortunately, when a drive starts to fail, reading sectors takes a very long time.  IF that is your case, since Ubuntu won't mount the NTFS partition, your only recourse to recover that data will be to attach that drive to a Windows PC and use a Windows utility to recover the data to some other drive.

If you're interested in doing that, read on ...

Since your data was on a Windows partition, based on my experience at doing this successfully, my suggestions are the following:
[NOTE: If your PC has a working copy of MS Windows on it, skip to step 4]
1) Find someone with a working MS Windows PC
2) Remove your drive from this PC.
3) Connect your old drive to the MS Windows PC.
4) Download and install the trial version of GetDataBack for NTFS from Runtime Software in MS Windows.
5) Run GetDataBack and select the option to find Deleted files.
6) When done, browse the filesystem in the app to see if your directories and files were found.  If so, view some to confirm the contents are intact.
7) If they are, you will have to purchase GetDataBack to do the actual recovery. You won't have to reinstall it; instead, they will email you an activation code which you can use to turn on the recovery feature.

And, last time I checked, GetDataBack for NTFS was $80, USD.

Your data ... your money ... your choice.

Hmm, yes. I was kind of starting to realise this would be the choice. The fact is, I knew the hard drive was dying when I put Ubuntu on it, and I told her to back up all data immediately, as the drive probably wouldn't last much longer. 

As usual though, she decided not to listen =='  

Thanks for the reply. I think the best idea would be to buy a new HDD and when I finally get my PC sent over from the UK, I can try and recover the data for her.

---


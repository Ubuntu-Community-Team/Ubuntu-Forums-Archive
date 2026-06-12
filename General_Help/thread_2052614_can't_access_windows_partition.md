---
title: "can't access windows partition"
date: 2012-09-03
forum: General Help
---

### Post by childofGod on 2012-09-03
I just upgraded to 12.04 the other day.  There is a windows partition on this computer.  It's still there.  I can see it from the linux partition.  In all previous versions of Ubuntu I could access files on the windows partition.  I can't do it any more.  Any ideas how to do it?  I can't go in by booting from windows any more due to certain corrupted files, so that is not an option.

---

### Post by coffeecat on 2012-09-03
> **childofGod said:**
> I can't do it any more.

What you haven't told us is how you tried to mount the Windows partition and access the files. Did you click on the Windows partition where it is listed in the left pane of a Nautilus file browser? If you did, did you see an error message? If so, what was the error message?

If you can't boot into Windows, this could be because of a damaged NTFS filesystem. If this is the case, then Ubuntu will not mount it but will give you an error. If it is the case you have a damaged NTFS filesystem, there are ways to deal with that, but before I speculate further perhaps you could clarify the points above.

---

### Post by childofGod on 2012-09-03
Actually the windows partition doesn't show in the left pane of a Nautilus file browser.  At first I thought the windows partition had been overwritten but after plugging around for a while I found it.  Unfortunately I can't recall how I got there.  It's still there, however, and I can open in it enough to see all the files are still there.  However, I can't open those files.  Before I upgraded I always had it in the left pane of a Nautilus file browser and could read and write to it.  I also always had it listed as one of the "Places" on the taskbar.  NTFS is OK, it just won't boot from the OS any more.

---

### Post by coffeecat on 2012-09-04
NTFS mounting and accessing is not really different from previous versions of Ubuntu, so using 12.04 should not be the problem, although something may have gone wrong with the upgrade. What version of Ubuntu did you upgrade from? Do you mean an upgrade using the update manager, or did you do a fresh install of 12.04? That might seem a strange question, but some people use the word "upgrade" when they really mean that they had done a fresh install overwriting an older version.

You puzzle me with this:

>  Unfortunately I can't recall how I got there. It's still there, however, and I can open in it enough to see all the files are still there. However, I can't open those files. 

If you are not seeing the Windows partition in the left pane of Nautilus, how are you opening the partition?

A couple of things to try. The first is unlikely to be the cause of your problem, but worth checking. During upgrades some people have lost the ntfs-3g read-write driver somehow. The system then defaults back to the read-only kernel ntfs driver. Check in whichever package manager you prefer - Software Centre or Synaptic - to see that you have the package ntfs-3g installed. If it isn't installed, install it. The package manager may tell you that it needs to uninstall the package ntfsprogs - that's OK. In 12.04, the functionality of ntfsprogs is included in ntfs-3g.

Do you have a live CD or live USB of Ubuntu 12.04? If you do, boot up with it and choose "try Ubuntu" to get to the live desktop. Then see if you can see the Windows partition in the left pane of Nautilus and if you can access the files there. This would a useful exercise to see whether there is a problem with your Ubuntu 12.04 hard drive installation or the Windows partition itself. So useful in fact, that if you do not have a live CD/USB it is worth downloading the ISO and creating one simply to check this.

---

### Post by Costas100 on 2012-09-04
You should be able to access your windows partition any time. In fact I managed to replace a corrupted system file in my windows partition, after extracting it from the original CD. If you still have troubles, make sure you mount the windows partition from System/Administration/Disk Utility.
As a last resort download and burn a Puppy live CD, you will be able to reach every corner of your computer (you don't need to install anything).
Take care and all the best to you
Costas

---


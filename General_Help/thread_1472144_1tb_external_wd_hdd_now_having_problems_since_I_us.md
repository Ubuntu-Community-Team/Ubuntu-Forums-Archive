---
title: "1tb external wd hdd now having problems since I used it on windows, detailed inside."
date: 2010-05-04
forum: General Help
---

### Post by OCN on 2010-05-04
I have been using my WD External drive/mybook as they call it with Ubuntu, until now recently connected it to my laptop running windows vista, I know it sucks but I just got this laptop and using it instead of my tower to save power and just run the laptop 24x7 pretty much and the tower when I need it and during the day I keep it on but anyway's. I copied a lot of files over to the external drive, disconnected it and pluged it back over to my laptop running windows and none of the files were shown, the files I just copied but the other stuff is still on it. 

I get this message when reconnecting it to Ubuntu when trying to use it. 

> Error mounting: mount exited with exit code 13: $MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.Have I damaged the drive, I hope not and hope to fix this problem to run on both OS.

Have I damaged the drive, I hope not and hope to fix this problem to run on both OS.

I have been using Ubuntu for about 6 months but still feel like a noobie, and a problem like this, I feel lost.

any help to fix this is much appreciated.

---

### Post by dcstar on 2010-05-04
> **OCN said:**
> I have been using my WD External drive/mybook as they call it with Ubuntu, until now recently connected it to my laptop running windows vista, I know it sucks but I just got this laptop and using it instead of my tower to save power and just run the laptop 24x7 pretty much and the tower when I need it and during the day I keep it on but anyway's. I copied a lot of files over to the external drive, **disconnected it** and pluged it back over to my laptop running windows and none of the files were shown, the files I just copied but the other stuff is still on it. 
..........

Did you unmount or eject it before "disconnecting" it?

---

### Post by OCN on 2010-05-04
No I did not, will this cause serious issues.  I will no longer do this, Ive done it in all 2 times. 

In Windows, do I need to run CHKDSK /f from CMD

---

### Post by srs5694 on 2010-05-04
You should ***always*** use a software unmount option (sometimes called "eject," "safely remove," or something similar; or "umount" if you do it from a Linux text-mode shell) before you physically disconnect a disk. If you don't do so, chances are very good that you'll lose files you've recently copied to the disk, and there's a lesser (but still significant) risk that you'll lose many more files. This is because Linux caches disk accesses, so at any given moment, data you've written to the disk may not actually be on the disk, and even if the files have been copied, the data structures referring to them might not yet be finalized. Only unmounting the disk ensures that everything will be tiedied up. If the disk uses NTFS, as yours appears to, then you won't be able to use the disk again until it's been checked in Windows, since Linux lacks the utilities to clean up an improperly disconnected NTFS disk. Windows *should* detect the need for this and run a check when you plug the disk in, but I can't guarantee that this will always happen. Running CHKDSK manually will ensure that it will be done.

---

### Post by Mark Phelps on 2010-05-04
For future reference, if you simply disconnect an external drive connected to MS Windows, without safely removing it first, you will likely encounter the same problems.

---


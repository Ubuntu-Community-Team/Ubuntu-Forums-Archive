---
title: "Unable to boot RAID1 after replacing a drive"
date: 2009-12-02
forum: General Help
---

### Post by JohnUt on 2009-12-02
I recently had a HD failure of one of my two drives in my RAID1.  After replacing the drive and manually copying the data with Gparted I restarted the computer and it held up on 

"Verifying DMI Pool Data ..............."

Not sure what needs done to make this RAID bootable again.

---

### Post by sedawk on 2009-12-02
How did you put data to the new drive when the computer
doesn't boot?

Did you use software or hardware RAID 1?
(what does the documentation say about replacing
 a broken drive - there should be instructions or
 software for it. When it is a hardware raid it does
 the recovery itself and doesn't trust any data you
 stored on that disk. I have never used a plain
 PC where the mainboard supports RAID 1 - is it
 possible your PC hangs because it is
 executing the recovery procedure? Any issues
 with cabling or jumpers on the disk (master/slave
 for IDE)?).

---


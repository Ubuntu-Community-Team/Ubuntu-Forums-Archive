---
title: "System halts when emptying trash or deleting files?"
date: 2009-07-17
forum: General Help
---

### Post by a11z on 2009-07-17
I experienced this in both Xubu and Ubu 9.04.

Problem:

When I delete some files/folders in the trash, my system halts. The system stops regardless of the size of the file being deleted. My only solution is to hard-shut-down, or to press the power button for five seconds.

Reference:

I updated my system to Kernel v2.6.28-13, but I also experienced this during v2.6.28-11.

Conclusion:

Has anyone encountered this? I appreciate any help from anyone.

---

### Post by prshah on 2009-07-17
> **a11z said:**
> 
Has anyone encountered this? 

Well, I haven't. 

When you say your system halts, do you notice if the HDD activity light is constantly on? (Flickering is fine and normal, I mean solidly on). In that case, it is likely you have a bad sector at just about that point. You can run a quick, safe and painless check by booting with a live CD and running a badblocks test```
sudo badblocks -v /dev/sda1
``` Ensure that the target filesystem is NOT MOUNTED. Replace /dev/sda1 as suitable to your system.

---

### Post by tkrisz on 2009-07-17
Release notes say something about deleting files for ext4 users.

---

### Post by a11z on 2009-07-17
> **tkrisz said:**
> Release notes say something about deleting files for ext4 users.

Yes, indeed I have ext4 for both "/" and "/home" partitions. Could this be a bug for ext4 partition style?

I saw this symptom in two different systems and different hdd, both of which are healthy without a dead block. Just in case, I did check the badblock code provided above: The result is clean - my hdds are okay.

Any other thought? Should I downgrade to "ext3" partition formats?

Reference:

I never experienced this with 8.10 and 8.04 using ext3. Has anyone experienced a system halt while emptying the trash?

Thanks again in advance.

---

### Post by a11z on 2009-07-17
Similar cases elsewhere:

[http://ubuntuforums.org/showthread.php?t=1211459&highlight=ext4+emptying+trash+system+halt](http://ubuntuforums.org/showthread.php?t=1211459&highlight=ext4+emptying+trash+system+halt)

[http://ubuntuforums.org/showthread.php?t=1189506&highlight=ext4+emptying+trash+system+halt](http://ubuntuforums.org/showthread.php?t=1189506&highlight=ext4+emptying+trash+system+halt)

[http://ubuntuforums.org/showthread.php?t=1170238&highlight=ext4+emptying+trash+system+halt](http://ubuntuforums.org/showthread.php?t=1170238&highlight=ext4+emptying+trash+system+halt)

[SOLVED / SOLUTION]: Reinstall Ubu and downgrade to "ext3" until solved.

[http://www.ubuntu.com/getubuntu/releasenotes/904#Lock-ups%20when%20deleting%20files%20from%20ext4%20filesystems](http://www.ubuntu.com/getubuntu/releasenotes/904#Lock-ups%20when%20deleting%20files%20from%20ext4%20filesystems)

Thanks to those of you who replied.

---


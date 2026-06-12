---
title: "SSD Commit=100"
date: 2012-01-06
forum: General Help
---

### Post by Bobhuber on 2012-01-06
For those of you with SSD drives that have changed the commit (journel commit) time in your fstab file you will find that after reboot the system automagically changes it back to 0 (5/sec).Run mount from a terminal and you will see the statement added to the end of your original fstab mount options.Heres what I've found from Mr. Google and the fix.Thanks to the Aptosid forum.
The issue is triggered by a re-mount that happens during the boot process, and then the power management rule at /usr/lib/pm-utils/power.d/journal-commit is invoked. The default commit value for "AC" is commit=0, and that is appended to the existing mount. So, I edited the file and changed the value to commit=100 (same as I now have it set in /etc/fstab). Now the three ext4 filesystems on my system are mounted correctly at the end of the boot process and I could remove the statement entirely from the fstab entries.
FYI, this file is also invoked on resume from suspend, so the issue is seen in that situation also.

WARNING- be prepared to lose data in the event of a power failure without battery backup if you use this statement with your SSD drive.

---


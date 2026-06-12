---
title: "My setup appears to have failed for some unknown reason..."
date: 2009-08-06
forum: General Help
---

### Post by scratman on 2009-08-06
My installation of Ubuntu appears to have failed. I've been using Ubuntu for around 3 years, annd this is not a fresh install but an upgrade to 9.04 which was performed in April.

My setup was working fine until a few days ago, but I cannot now log in.  I use OpenTTD, and my machine has become unstable since I updated to 0.7.2 3 days ago.  I doubt that this has had any impact at all, but I figured that I would mention it.

Upon starting my machine, it attempts to boot normally, but then runs into problems.  Below is all of the infornation provided at the screen it halts at.

Starting up...
[   0.416001]  ..MP-BIOS bug: 8254 timer not connected to IO-APIC
Loading, please wait...
19+0 records in
19+0 records out
kinit: name_to_dev_t(/dev/disk/by-uuid/8a9259d65-9322/4c77/8e1e-d9cce96630a7) = dev(8,5)
kinit: trying to resume from /dev/disk/by-uuid/8a9259d65-9322/4c77/8e1e-d9cce96630a7
kinit: No resume image, doing normal boot...
mount: mounting /dev/disk/by-uuid/289de4f3-167a-4ce4-ad66-7962f612caa0 on /root
failed: Invalid argument
mount: mounting /dev on /root/dev failed: No suce file  or directory
mount: mounting /sys on /root/sys failed: No suce file  or directory
mount: mounting /proc on /root/proc failed: No suce file  or directory
Target filesystem doesn't have /sbin/init.
No init found. Try passing init=bootarg.

BusyBox v1.10.2 (Ubuntu1:1.10.2-2ubuntu7) built-in shell (ash)
Enter 'help' fora list of built in commands.

(initramfs) [  11.475081] sd 8:0:0:0: [sdb] Assuming drive cache : write through
[  11.479079 sd 8:0:0:0: [sdb] Assuming drive cache: write through

I'm really not sure what's caused this to occur.  I've tried booting to other versions of the Kernel (there are 3 previous kernels on my machine) and booting into safe mode (no joy there either).  I'm currently downloading an iso of 9.04 with a view to booting to that and trying to recover.

I just wondered whether anybody else has had issues with this, and whether anybody has any advice to resolve this issue.

Many thanks in advance.

---


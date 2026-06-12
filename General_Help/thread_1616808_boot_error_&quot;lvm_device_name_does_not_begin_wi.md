---
title: "boot error: &quot;lvm device name does not begin with /dev/mapper/"
date: 2010-11-08
forum: General Help
---

### Post by JayRobert on 2010-11-08
I was offline a few months and recently ran all the updates since July.  I have two kernels in my boot menu, realtime and lowlatency.  Since running updates, I can boot the realtime kernel (it is first on the menu) but when I try to run the lowlatency kernel, I get the following error:

cryptsetup: lvm device name (/dev/disk/by-uuid/.......) does not begin with /dev/mapper/

I usually run the realtime kernel only when recording stuff, and the lowlatency otherwise, since I have fewer problems running Skype with the latter.

Is there a way I can fix this?  All my drives are encrypted lvms, and /home is also on a RAID 5 array (lvm, encrypted).  I remember having to tweak some things in grub and maybe fstab when I first set it up, but I haven't been able to fix this particular problem since the updates ran.  It has been four or five months since I modified those files, and I can't remember exactly what to do, or what to look for.  I haven't been able to locate this problem on any other threads, either.

Any help will be greatly appreciated!

---

### Post by ronparent on 2010-11-08
Just a possibility that dmraid has intervened to look for fakeraid devices in /dev/mapper. Since you don't seem to be using fakeraid you might try uninstalling the unneeded dmraid.

---


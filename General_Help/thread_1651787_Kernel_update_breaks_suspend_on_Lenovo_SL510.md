---
title: "Kernel update breaks suspend on Lenovo SL510"
date: 2010-12-23
forum: General Help
---

### Post by WA1DH on 2010-12-23
I just updated my kernel to the latest version (2.6.35-24). Now my suspend function on my Thinkpad SL510 no longer works. The system simply hangs with a solid cursor in the corner of a black screen. USB devices remain powered on, HDD keeps spinning, and all indicator lights remain lit. When this happens, the only thing I can do is hold the power button down for a hard power off.

My first thought would be to troubleshoot this with dmesg, but I don't know how to record dmesg after a power off. The message buffer is reset when I reboot.

Any ideas as to what the problem is and how to fix it? I will need to roll back the update if I can't fix this.

Thanks.

---

### Post by garvinrick4 on 2010-12-23
I would go back to kernel that worked and use it. Go into synaptics and type in offending kernel in box and right click and remove that kernel and just wait for next one to come out. Pretty tedious and a lot of work to find out why a kernel does not do a specific thing in
my case or experience level. New kernels do come out quite often. Just a suggestion maybe someone pops in with better answer for you. Have a nice day and a Merry Christmas.

---


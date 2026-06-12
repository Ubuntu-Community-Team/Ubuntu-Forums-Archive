---
title: "do I need libc6-i686?"
date: 2006-05-26
forum: General Help
---

### Post by D!mon on 2006-05-26
I have Athlon XP so I run 2.6.12-10-k7 kernel; also I installed package libc6-i686.
The question is:  do I really need it (orphaner says that it's unnecessary) and how can I check if my system really uses it instead of stock libc6?

---

### Post by warp99 on 2006-05-26
Here is what the Ubuntu packages site has to say

"This set of libraries is optimized for i686 machines, and will only be used if you are running a 2.6 kernel on an i686 class CPU (check the output of `uname -m'). This includes Pentium Pro, Pentium II/III/IV, Celeron CPU's and similar class CPU's (including clones such as AMD Athlon/Opteron, VIA C3 Nehemiah, but not VIA C3 Ezla)."

[http://packages.ubuntu.com/breezy/libs/libc6-i686]("http://packages.ubuntu.com/breezy/libs/libc6-i686")

Does this answer your question? :cool:

---

### Post by D!mon on 2006-05-26
Yup, thanks:) I meant: if I just installed this package, it will be used after reboot? 
(actually, my X system failed to start after reboot, I recompiled NVidia driver and repeated prelink process, so after next reboot everything was just fine)

---


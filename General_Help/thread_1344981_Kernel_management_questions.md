---
title: "Kernel management questions"
date: 2009-12-03
forum: General Help
---

### Post by besson3c on 2009-12-03
Both 2.6.31-14 and 2.6.31-15 of the Ubuntu 9.10 kernels have been disasters for me. I have Ethernet and clocksource problems in these which lead to a lot of instability. I'm currently running 9.10 while booted into the last kernel that shipped with Ubuntu 9.04, 2.6.28-16, but I have some questions/problems...

1) Is there anyway to regain sound while booted into this kernel? Some time ago I attempted to rebuild the sound kernel drivers, but I still wasn't able to get this to work. I gave up thinking that perhaps pulseaudio or some other package was tethered to the latest kernels and I didn't want to mess around with rebuilding all of these packages. In general though, are there some usable strategies to mixing and matching kernels against OSes this way?

2) When I upgrade to 2.6.31-16 my 2.6.28-16 kernel will be bumped off of my Grub list. Is there an easy way to sort of pin this there for a while? I'm assuming I can just keep a copy of the vmlinuz file/directory and just manually add 2.6.28-16 back to my menu.lst?


Any other strategies you have for managing hanging onto your favorite kernel iterations and testing new ones would be appreciated! I have no sense how long it will take to sort out this 2.6.31 kernel problems, and I realize it could be a while...

---


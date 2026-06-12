---
title: "Unwarranted Kernel Panic."
date: 2010-01-14
forum: General Help
---

### Post by myrules92 on 2010-01-14
I'm running 9.10, and I've got Ubuntu located on an external hard drive. GRUB seems to work when run from both my internal and external, however, if it's run from my internal, the system begins to boot, but later stops, freezes, and gives me the ol'

"Kernel Panic- Not Syncing - Attempted to kill init!"

No, not fun. I'm not sure why, but BIOS's main boot drive is my external, although it seems like sometimes it's not booting from that unless I do it manually. Therefore, about 3/4s of the time, if I let the system boot up automatically, Kernel Panic. But if I choose the hard drive manually, it runs smooth as butter.

Any fixes to this problem?

---

### Post by john newbuntu on 2010-01-14
I am not sure on what you have on your internal drive, but can you try and re-install Grub2 from an Ubuntu liveCD (step 13 from our friend drs305)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
Then reboot without the external drive and run "sudo update-grub2"

---


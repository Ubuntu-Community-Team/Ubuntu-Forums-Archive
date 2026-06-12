---
title: "Replacement Motherboard"
date: 2010-12-06
forum: General Help
---

### Post by Quarkrad on 2010-12-06
Was running dual boot 10.10 and winxp on a MSI P4M900 motherboard.  Have two HDs - one with OSs and some storage and the other purely backup for storage and Ubuntu home.  Motherboard died and going to be replaced by Gigabyte G31 board. I will be using the same video, audio PCI cards and memory from old board.  Should I look to a clean install of 10.10 and then *bring back to life* from my backup files (bookmarks, email etc) or could I plug in hard drives and boot normally?  There is conflicting advice when I google - some say its OK just to boot, the kernel will sort out the new mboard drivers, others say you need a clean install.

---

### Post by coffeecat on 2010-12-06
You don't need a clean install - the kernel will indeed sort out drivers. Hardware is probed on each bootup. The only real problem is proprietary video drivers but since you are going to be using the same video card, you've avoided that issue. The  audio card may pick up a different PCI bus reference on the new motherboard and that *might* lead to a need to reconfigure your sound settings - or maybe not.

But Windows **will** have a fit of the vapours when encountering a new set of hardware. You will need to re-activate or maybe even re-install.

---

### Post by Quarkrad on 2010-12-06
Many thanks - I only use win for iTunes and occasional video editing - Ubuntu is 99% of my PC time.  I can reload XP at leisure.

---


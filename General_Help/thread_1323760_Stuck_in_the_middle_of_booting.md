---
title: "Stuck in the middle of booting"
date: 2009-11-12
forum: General Help
---

### Post by ALF102 on 2009-11-12
When I boot up, after the dual-boot screen and after the Grub menu, this message appears:

          [ Linux-bzImage. setup=0x3400, size=0x3b26eO ]
          [ Initrd, addr=0x37864000, size=0x78b4e7 ]
[           1.843325] Kernel panic- not syncing: VFS: Unable to mount root fs on unknown-block (8,1)



Then it got stuck there...what does this message means?
This happens right after the updates

---

### Post by benjamin222 on 2009-11-13
Same problem here, no one seems to have any answers... All I did to cause the problem was run updates

---

### Post by LoloftheRings on 2009-11-13
Do you have any old kernel boot options? I believe Ubuntu leaves about 3 old kernels in your boot menu, try one and see if it works. This is clearly a kernel error. I had it before when I was messing with custom kernels.

---

### Post by ALF102 on 2009-11-13
Nope, no old kernel option. All I have is the kernel, the recovery mode and the third one is Windows XP. Even recovery mode doesn't work

---


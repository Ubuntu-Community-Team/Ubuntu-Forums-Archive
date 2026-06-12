---
title: "Failure to install grub stage 1.5"
date: 2010-02-06
forum: General Help
---

### Post by BardSeed on 2010-02-06
Sorry if this has already been posted and feel free to move this thread somewhere more appropriate.

I'm dual booting Fedora 12 and Ubuntu 8.04. After some initial problems getting back to ubuntu, I now have a couple more that need clearing up. For background, see [here(click)](http://www.linuxformat.com/forums/viewtopic.php?p=84954#84954).

I'm having problems installing grub stage 1.5. I've tried from Fedora and Ubuntu, but 1.5 never runs. Here's my output from an Ubuntu terminal:
```

grub> root (hd0,0)

grub> setup (hd0,0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,0)"... failed (this is not fatal)
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,0)"... failed (this is not fatal)
 Running "install /boot/grub/stage1 (hd0,0) /boot/grub/stage2 p /boot/grub/menu
.lst "... succeeded
Done. 

```

I'm also having problems shutting down, but I decided to put taht in another [thread(click)](http://ubuntuforums.org/showthread.php?p=8783339#post8783339) as my initial dual boot thread didn't get a single reply.

---


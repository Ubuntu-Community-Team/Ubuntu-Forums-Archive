---
title: "grub 2 won't reinstall"
date: 2010-04-13
forum: General Help
---

### Post by z987k on 2010-04-13
I can't get grub2 to reinstall after installing windows - which deleted the bootloader obviously.

I mounted /dev/sda2 to /media/sda2
Then I ran sudo grub-install --root-directory=/media/sda2 /dev/sda2

Here's the error:
```
grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea.
grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged.
grub-setup: error: Cannot read `/grub/core.img' correctly
```

The first warning seems like I can ignore, but why is it not reading /grub/core.img correctly?  I looked in /media/sda2/boot/grub for core.img and it does not exist there.

---

### Post by z987k on 2010-04-13
well I posted too soon.  Fixed my own problem already.

I don't know why but grub would not install to /dev/sda2, but when I told it to go to /dev/sda like I should.... it wrote to the MBR and not the partition and everything works.

Hope this helps someone else out.

---


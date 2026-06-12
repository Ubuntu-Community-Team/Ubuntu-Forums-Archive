---
title: "make hard drive bootable again"
date: 2010-04-06
forum: General Help
---

### Post by kmiya100 on 2010-04-06
My karmic ubuntu studio will no longer boot.  I believe I may have intermittent hard drive issues.  I've backed up all my important files so I'm not extremely worried; however, I would like to try to get my setup bootable once more.  I've reinstalled grub, and on trying to boot, I get the grub kernel selection.  Regardless of what I choose, the system won't boot.  I believe grub is alright, but something else is not.  What else could I try to make it boot again?  I've mounted the drive, chrooted to it, updated and upgraded, but it still won't boot.  I may be doing that wrong, or there may be something else I need to do.  Any help would be greatly appreciated.

---

### Post by johngreth on 2010-04-07
you should chroot into the system and run
```
sudo grub-install /dev/sdX
```
as is outlined here: [https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)
and
```
sudo update-grub
```

hope this helps.

---

### Post by kmiya100 on 2010-04-07
Thanks for the suggestion.  I tried as you said, but still couldn't get it to boot.

---

### Post by johngreth on 2010-04-08
Before I assumed thet you were using grub2. Is that the case?

---


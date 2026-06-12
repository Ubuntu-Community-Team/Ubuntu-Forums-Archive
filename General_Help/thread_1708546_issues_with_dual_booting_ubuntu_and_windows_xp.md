---
title: "issues with dual booting ubuntu and windows xp"
date: 2011-03-16
forum: General Help
---

### Post by Goggz on 2011-03-16
hiya, sorry if this is in the wrong place...

a little while ago i updated ubuntu to 11.04 alpha 3 which did not go so well, main problem being that GRUB no longer showed Windows XP, OS-prober would not recognise it etc etc. after many hours of editing grub.cfg, trying to manually mount the partition and so on following a lot of advice on here i had no luck.

just in case any one else had had a similar issue:

turns out that it was not ubuntu, GRUB or OS-prober that were the problem but windows itself (should have never doubted ubuntu in the first place). turns out the boot sector had corrupted, easily being fixed by setting up a bootable usb stick with Windows recovery console on it and running fixboot (i think that was the command). after running this everything worked again, hurrah!

---


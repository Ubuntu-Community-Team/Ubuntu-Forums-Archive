---
title: "GRUB Error 17; computer won't boot."
date: 2010-06-11
forum: General Help
---

### Post by dierubikdie on 2010-06-11
I have a Sony Vaio AR370 with two 100GB SATA HDD's. For a while, I had Vista Home Premium installed on one and Ubuntu on the other. Every time I booted, GRUB made me select between the two. I recently was in Vista and reformatted the HDD on which Ubuntu was installed, completely erasing Ubuntu from my computer (I needed the space). I shut down the computer and restarted, only to get GRUB Error 17. It seems to load GRUB, then says "please wait," and then just says Error 17. Nothing I do gets any response but Ctrl+Alt+Del, which simply restarts the computer, which sends me right back to Error 17. What can I do to remedy this? I have come here for foolish computer mistakes before and was not let down, so I'm asking for one more miraculous solution from you folks. What can I do to fix my computer?

-Brady

---

### Post by wilee-nilee on 2010-06-11
If you have a vista install disc you can reset the master boot record.
You might want to post the boot script to just confirm, some things though in code tags please.;)
[noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

If you don't have a install dvd you can probably use this.
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
Method 2 in this link explains getting to repair with a disc.
[http://www.sevenforums.com/tutorials/668-system-recovery-options.html](http://www.sevenforums.com/tutorials/668-system-recovery-options.html)

Chances are though that the auto repair wont work but some commands will so, again the script will direct us there.

Post the script though before doing anything other then downloading the recovery if needed.

I know the links are for W7 but I believe the process is basically the same for Vista

---


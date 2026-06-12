---
title: "Double GRUB Boot Options"
date: 2010-10-01
forum: General Help
---

### Post by MindCalamity on 2010-10-01
Ok first, the facts: I'm dual booting Windows 7 and Ubuntu Lucid, after a few restarts the GRUB menu got messed up (it shows 2x Ubuntu and memtest options and 1x Seven). I tried updating GRUB but it didn't work, and I'd hate to mess up my system by manually editing grub.cfg... Any ideas ?

---

### Post by Quackers on 2010-10-01
It may be that recent updates installed a new kernel (hence the second Ubuntu entry in grub). Try booting the one with the highest number.

---

### Post by MindCalamity on 2010-10-01
> **Quackers said:**
> It may be that recent updates installed a new kernel (hence the second Ubuntu entry in grub). Try booting the one with the highest number.

I think you are right, but the issue is the bloated menu... I want to remove the old entry... (I installed all the recent updates, so I think you're right.)

---

### Post by Rubi1200 on 2010-10-01
Each time there is a kernel upgrade it is added to the GRUB menu along with the entry for Recovery Mode.

In most cases, it is advisable to keep at least one extra entry in the event that something goes wrong with an upgrade and you need to boot into a previous kernel.

Running the update-grub command does not remove the extra entries.

If you want, use Synaptic and search for linux-image and linux-headers and remove the files for the version you do not want (there will be a total of 3 files per version).

---

### Post by Quackers on 2010-10-01
See this thread for some ideas
[http://ubuntuforums.org/showthread.php?t=1541785&highlight=deleting+grub+menu+items](http://ubuntuforums.org/showthread.php?t=1541785&highlight=deleting+grub+menu+items)

---

### Post by MindCalamity on 2010-10-02
Thanks, then I'll leave it just in case, the update seems successful though.

---


---
title: "reinstall screwed windows, while keeping ubuntu partition"
date: 2009-06-29
forum: General Help
---

### Post by saoró on 2009-06-29
My windows partition is fairly thoroughly screwed. It bsod on everything, I cannot even boot from xpcd or ERD commander. Seems to indicate hardware probs, but memtest checks out and I can access all my files from ubuntu, which works fine. Ive googled for years, GAH! but I havnt found any solutions. I would like to do a clean reinstall of my xp side, and leave ubuntu untouched, is this possible? especially seeing as I cant boot my Xp cd?! Would I be able to boot after deleting the partition? Any help in either restoring or reinstalling the xp side, while keeping ubuntu would be great.

Dual boot XPsp2/Ubuntu8.10  130/30gb respectively 
Dell vostro 1500 T7500 2.2ghz, 2gb ram
Integrated sound/Nvidia 8600m gt with restricted drivers

---

### Post by ajgreeny on 2009-06-29
I'm not sure why deleting the windows partition would make any difference to booting the WinXP install CD, so am a bit baffled about that, but as a last resort I suppose it may be worth a try.  You can certainly install WinXP to just one partition without messing up your ubuntu partition, in fact a winXP Cd will not even see your ubuntu partition.  It will remove grub, however, and replace it with the windows MBR, but don't panic, it's a few seconds job to put grub back afterwards with the ubuntu live CD.

I suppose it's possible that the windows system has become borked that even the windows CD can not see it, and as you can do nothing with it at the moment anyway, you may as well delete it and try this method.

Good luck!  I hope you get things up and running again as you want it.

---

### Post by saoró on 2009-06-29
It certainly seems like last resort time at this stage, so ill give it a shot and hope for the best. Cheers.

---

### Post by t4thfavor on 2009-06-30
Install windows on the old windows partition,and then boot into the livecd follow one of the million repairing grub tutorials, and your golden.

---


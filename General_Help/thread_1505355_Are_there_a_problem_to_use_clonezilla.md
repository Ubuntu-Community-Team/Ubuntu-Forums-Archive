---
title: "Are there a problem to use clonezilla?"
date: 2010-06-09
forum: General Help
---

### Post by rudysuryanto on 2010-06-09
I want to make image partition of my ubuntu Linux at partition ext4, 20 gb use clonezilla, then I want restore it at partition ext4, 80 gb, will be have a problem?
Thank's.

---

### Post by Quarkrad on 2010-06-09
I find Clonzilla very good for both imaging and restoring.  The only issue I had (which was a big one for me) is that the boot sector is not imaged so when you do a restore you have no boot sector which is a major issue if you dual/multi boot (I boot Ubuntu and winXP).  You can, in theory, easily rebuild grub 2 boot sector, but in practice, I found this a real pain/problem.  Not only what build to use (there are a number of builds recommended) but sometimes they work sometimes they do not.  It takes so long you may as well just backup **home** and a few other folders and do a clean install - it is quicker (for me) than faffing around rebuilding grub 2.

---

### Post by rudysuryanto on 2010-06-09
@rickymaccullum: you must first download clonezilla iso file at [http://clonezilla.org](http://clonezilla.org), then you burn cd image iso file to CD, reboot your computer use that CD. Then follow instruction on screen.

---


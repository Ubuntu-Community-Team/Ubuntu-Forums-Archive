---
title: "upgrade windows"
date: 2011-09-24
forum: General Help
---

### Post by makrami on 2011-09-24
I have installed Ubuntu 11.4 by wubi in windows XP. now, I want to upgrade my windows xp to windows 7. should I remove my Ubuntu and install windows windows 7, then reinstall Ubuntu?

---

### Post by Rubi1200 on 2011-09-24
Hi and welcome to the forums :-)

I would think an upgrade will involve formatting at some stage, so the Wubi install would likely be written over (not a Windows user so can't say for sure about this).

However, what I do suggest is that you make a backup copy of the Wubi root.disk and keep it somewhere safe.

After the upgrade, if all went well and Wubi was not overwritten then fine.

If it was, we can show you how to restore the original root.disk so you will not have lost any custom settings, folders etc.

---

### Post by WorMzy on 2011-09-24
That's what I would recommend. I'm not sure how smooth the transition from XP to 7 is, but removing Ubuntu from the NTLDR beforehand can only simplify matters.

If you're enjoying Ubuntu, you might want to take this opportunity to install it to it's own partition.

Oh, and make sure to back up any important data from both your Wubi installation and Windows installation before you a) delete Wubi, and b) install the upgrade. Better safe than sorry. :)

---

### Post by asifnaz on 2011-09-24
I was asking similar questions like one year ago . I suggest you to leave wubi as it runs inside Windows which is very unstable . Install Ubuntu in physical partition and you will feel it very responsive and stable .

---

### Post by Mark Phelps on 2011-09-24
There is no "upgrade path" from XP to Win7, so basically, even if you do "upgrade" your PC, it's essentially the same as a clean install.

Laplink sells an app that DOES allow an in-place upgrade from XP to Win7, but I've not used it and, in general, on real Windows forums, such in-place upgrades are strongly discouraged.

This means that you will LOSE the Wubi installation however you attempt to do the upgrade.

---


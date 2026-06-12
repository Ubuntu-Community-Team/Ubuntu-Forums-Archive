---
title: "my ubuntu not starting"
date: 2011-11-01
forum: General Help
---

### Post by bijan_sky on 2011-11-01
Hi all

I restarted my computer, and when it was turning back on, Ubuntu wouldn't start anymore. I can select OS but select the ubuntu os is not starting! only A black screen is displayed!:confused:
when I come to Recovery mode and select the remount /Read/Write and mount all other file systems, following error occurred :
[COLOR="SlateGray"][38.320097] Ext4-fs (sda9) : re-mounted opts(null)
moutall: mount/ [463] : Permission denied.
/lib/recovery-mode/options/remount: 29 : gettext : Permission denied[/COLOR]
Can i correct it?:confused:
Please Help

---

### Post by Mark Phelps on 2011-11-01
Next time you go into Recovery Mode, select the option to Repair broken packages. That may then fix your system so you can login again.

---

### Post by bijan_sky on 2011-11-02
> **Mark Phelps said:**
> Next time you go into Recovery Mode, select the option to Repair broken packages. That may then fix your system so you can login again.
I can't see "option item"!

---

### Post by Mark Phelps on 2011-11-02
You should be seeing a LOT of text scrolling by on the screen, and then finally, a list of options.  One of them will be to repair broken packages.  

If you're not getting that far, you will probably have to reinstall from scratch.

---


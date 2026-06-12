---
title: "Installing ubuntu breaks windows."
date: 2010-05-03
forum: General Help
---

### Post by rock4christ on 2010-05-03
I installed lucid x64 alongside windows 7 x64, and ubuntu works flawlessly, but windows 7 gets to the starting windows splash, and restarts. to make it work, i have to run startup repair.

---

### Post by pcura on 2010-05-03
whats your question?

---

### Post by rock4christ on 2010-05-03
sorry.... any idea what could cause that?

---

### Post by rnerwein on 2010-05-03
> **rock4christ said:**
> I installed lucid x64 alongside windows 7 x64, and ubuntu works flawlessly, but windows 7 gets to the starting windows splash, and restarts. to make it work, i have to run startup repair.

hi
you are not alone. same problem on my box. i wrote a thread yesterday.
on my box are XP -> suse 11 -> karmic Koala -> solaris 10 and lucid lynx
the only problem ( solaris configure always by my self ) is XP. i have to start it in the recovery ( i mean windows recovery ) mode and
it works.
my thread was called: grub2 - the never ending story  :P

ciao
i think the problem is - here is the layout of my primary disk.
[COLOR=Blue]/dev/sda1[/COLOR]               1        1828    14680064   27  [COLOR=Red]Unbekannt[/COLOR] ( Unbekannt = unknown )
 /dev/sda2   *        1828       46484   358701056    7  HPFS/NTFS
but in grub.cfg the entry for vista is

menuentry "Windows Vista (loader) (on /dev/sda1)" 
insmod ntfs
richi@tschang:~ 17:11->         set root=[COLOR=Blue]'(hd0,1)'[/COLOR]

i intalled lynx on a third ( external usb scsi) disk

---

### Post by pcura on 2010-05-03
have you updated your windows.....just asking. that might be one issue though.

---

### Post by rock4christ on 2010-05-03
yes. windows is 100% up to date

---


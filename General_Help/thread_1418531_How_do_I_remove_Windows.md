---
title: "How do I remove Windows?"
date: 2010-02-28
forum: General Help
---

### Post by d_fyant on 2010-02-28
Greetings!  Having just liberated myself from mICROSOFT, I wish to put the final nail in the coffin by removing Windows altogether, but, I'm not sure how to go about this.  I have the disk partitioned and fdisk reveals the following: 

/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6        9333    74927160    7  HPFS/NTFS
/dev/sda3            9334        9725     3148740   db  CP/M / CTOS / ...


I'm not sure even which partition Ubuntu resides and which one where Windows is.  Any help is greatly appreciated!!!

---

### Post by spiky001 on 2010-02-28
windows is in sda2 but you have a recovery in sda1 by the looks

---

### Post by d_fyant on 2010-02-28
So just repartioning sda1 and sda2 should do it?  Are there any special considerations I should take before?

---

### Post by oldfred on 2010-02-28
If those are all your partitions you do not have Ubuntu in a separate partition. Do you have wubi? Wubi is inside the windows partition?

---

### Post by Lunx on 2010-02-28
Others here may have a better idea than myself, but if you have a liveCD, why not back-up your stuff and do a fresh install? I did one this morning to revert from Lucid back to Karmic, took just over an hour in total (including the updates and restoring my personal files). At least if you do it that way, you should be pretty confident you won't get any grub errors, or have trouble booting.

---

### Post by d_fyant on 2010-03-02
Well, I just broke down and did a clean install rather than fighting with it.  Thank you all for the help!  You've helped convert 4 former mICROSOFT users!!!  Ubuntu Rocks!!!  Thanks Again!

---

### Post by drdanielfc on 2010-03-02
> **d_fyant said:**
> Well, I just broke down and did a clean install rather than fighting with it.  Thank you all for the help!  You've helped convert 4 former mICROSOFT users!!!  Ubuntu Rocks!!!  Thanks Again!

Make sure you keep an xp computer around you will always need ms at the worst moments

my $0.02 :-)

---


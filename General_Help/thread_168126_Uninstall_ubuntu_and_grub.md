---
title: "Uninstall ubuntu and grub"
date: 2006-04-29
forum: General Help
---

### Post by daniel3581 on 2006-04-29
Hi All,

I was just wondering if anyone would be able to help me. I am trying to uninstall ubuntu (v5.10) and the GRUB on a dual boot machine (with windows XP home), but still leave windows on there. I have gone to many sites, and they're all telling me different things, in very techy language. ](*,)  If anyone could provide me with a simple step by step way of removing ubuntu, it would be very much appreciated.

Cheers

Daniel.

---

### Post by Qrk on 2006-04-29
To uninstall Ubuntu just reformat the partition. You can make it fat32 using a Linux liveCD with gparted on it, such as the Ubuntu liveCD. You can also use the partitioning part of the  Ubuntu install CD to format the parition as Fat32. 

Removing Grub is more difficult. You'll need a Windows recovery environment. I don't believe Microsoft has a nice way to do this in XP home. 
I have heard good things about Bart's PE, which should work. [http://www.nu2.nu/pebuilder/](http://www.nu2.nu/pebuilder/)

Boot into the recovery environment and run the Windows (DOS) command: *fixmbr*

---

### Post by syg00 on 2006-04-29
Just boot your XP CD and select "Recovery Console".
From there run fixmbr.
Reboot.

---


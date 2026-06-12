---
title: "64 bit vs. 32 bit"
date: 2011-01-11
forum: General Help
---

### Post by watcher6342 on 2011-01-11
im having probs getting 32bit to work on my usb drive for my work comp (xp pro) would it be better to just try and install 64bit onto my home comp win 7 64bit ? also. does it need its own partition for usb drive or should it run straight from usb? also same question for the 64bit on my home comp. does it need its own partition? thank you.

---

### Post by 3Miro on 2011-01-11
If you run Ubuntu from a USB drive, you need to format it in a special way (or give it its own partition). On your home computer, you can either use separate partition or Wubi (install with windows). Wubi is slower and weaker that the stand-alone, but it can be easily removed later and is overall "safer" (otherwise if you mess partitions, you can lose important files). However, whatever you do, you should make sure to first backup anything important.

---

### Post by Mark Phelps on 2011-01-11
> **watcher6342 said:**
> im having probs getting 32bit to work on my usb drive for my work comp (xp pro)...
Would advise against installing Ubuntu on your work computer -- due to risk of overwriting the MBR with GRUB.

>  would it be better to just try and install 64bit onto my home comp win 7 64bit ? 
Any PC that will install 64-bit stuff will also handle 32-bit stuff -- but not vice-versa.  Need more details than "having probs".

> also. does it need its own partition for usb drive or should it run straight from usb? also same question for the 64bit on my home comp. does it need its own partition? thank you.
Any install needs its own partitions (except Wubi -- which, since you want to install to USB drive, does not apply).

---

### Post by cascade9 on 2011-01-11
> **Mark Phelps said:**
> Would advise against installing Ubuntu on your work computer -- due to risk of overwriting the MBR with GRUB.

Any PC that will install 64-bit stuff will also handle 32-bit stuff -- but not vice-versa.  Need more details than "having probs".

Point on the GRUB/MBR issue. If it was me, I'd install it at home, and make sure that GRUB goes to the flash drive. As long as the 'work' computer has the ability to boot from USB, its the easiest option. Alos the least likely to brign down the wrath of the sysadmin. 

I'm not sure that I'd install a linux distro on a work computer at all, or even run one from a flash drive. Check with the techie/sysadmin befoer you do that. 

AFAIK some 64bit architectures wont run 32bit, or even have a 32bit version, like Itanium and SPARC (yes, SPARC 32 did exist, but moved to 64bit in 1993). Not that watcher6342 has much chance of getting one of them. For x86 (AMD64, x86-64, etc etc) yeah, 32bit will work fine.

---


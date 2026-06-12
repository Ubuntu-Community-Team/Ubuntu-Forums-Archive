---
title: "Help Needed: Encrypting a Dual-Boot Configuration"
date: 2011-04-01
forum: General Help
---

### Post by coljohnhannibalsmith on 2011-04-01
Hello,

Is anyone aware of a software product that will encrypt the entire drive of a dual-boot Windows/Linux configuration?  TrueCrypt will only do this if both OS's are in Windows partitions i.e., Windows Vista/Windows 7, not Windows 'X'/Linux 'X' partitions.

In my current configuration the Ubuntu Partition is encrypted, but the Windows partition is not.  This has produced the interesting side-effect that I can read and transfer files to the Windows partion, from the Ubuntu partition, but not the reverse.  I consider this to be a desireable side-effect, at least in one direction.  I suppose I could use Windows 'BitLocker' to encrypt the Windows partition, but I have been reluctant to do this fearing that I would 'hose' both OS's at worst, and at best make the Windows partition invisible to the Ubuntu partition.  I lose either way.  What I would like, ultimately, is to have both partitions able to read and write to each other, and the entire drive encrypted.

Has anyone figured out how to do this?


Thanks, Hannibal

---

### Post by 3Miro on 2011-04-01
You can use Ubuntu alternate install to encrypt your Ubuntu partitions. I don't know how Windows encryption works. I am assuming you have to do encryption the regular way and then install some software on both systems to read an encrypted version of the other OS's filesystem.

---

### Post by uRock on 2011-04-01
Support question.

Moved to general help.

---


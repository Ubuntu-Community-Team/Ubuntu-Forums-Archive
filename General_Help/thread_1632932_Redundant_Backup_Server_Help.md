---
title: "Redundant Backup Server Help"
date: 2010-11-28
forum: General Help
---

### Post by dchrist21 on 2010-11-28
I am planning on using xubuntu 10.10 and some spare hardware to build a redundant network backup of personal files.  Let me illustrate:

I have a 500Gb external drive attached to my iMac running OS X 10.6.  For the purpose of this scenario the iMac's network name is "imac" and the external volume is called "ext-data".
I will have a 1Tb internal drive in the xubuntu machine.  The drive will hold both the xubuntu OS and all archived data.  The network name of the xubuntu system is "vault".

Once each week xubuntu will "wake up" from a stand-by state, connect to ext-data via an SMB share and synchronize a local copy of all files stored on ext-data.  Once the operation is completed the machine will return to a stand-by state until the next scheduled synchronization.  The machine will also perform a monthly restart automatically.

My question is what is the best way to accomplish this task?  I am assuming that rsync will be a central part of the solution, but am open to other suggestions.  I am also open to suggestions on the the choice of OS, network connection protocol, and whether the sync operation is a data "push" or "pull".

I have some experience with the desktop versions of ubuntu, and a limited familiarity with SSH and other features, but its safe to assume that I know very little about manually mounting drives or performing automatic scheduled tasks.  So, the more detail I can get from any answers, the better.

Also, I have a virtual installations of Xubuntu 10.10, Ubuntu Desktop 10.04, and Ubuntu Server 10.10 running under Parallels on my iMac, so I am able to test out ideas and proof-of-concept type things.

Thanks

-Dylan

---


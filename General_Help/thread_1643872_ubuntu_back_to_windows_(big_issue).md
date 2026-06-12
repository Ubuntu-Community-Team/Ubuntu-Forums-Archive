---
title: "ubuntu back to windows (big issue)"
date: 2010-12-12
forum: General Help
---

### Post by Kreios on 2010-12-12
Alright, my friend got a computer and finally got fed up with windows. So he decided to install ubuntu 10.10 on his separate 80GB hard drive and then delete his windows folder off his main 500GB drive <.< The problem he's having now is that his video card won't fully communicate properly with his computer, so he can't play starcraft 2 (if that really is the problem I have no idea, it could be a number things at this point). Anyway, I told him even if he is fed up with it, it doesn't make any sense to have a computer not do what you want. So my plan is to reinstall windows and have my way with it. 

The problem I'm having is that it won't install on the 500GB drive and I have no way to restore anything. All I have is a Windows 7 ultimate disk. I would like to set this up so that he can duel boot, that way if he encounters any problems he can load up ubuntu. Tell me anything you need to help me solve this and I'll give it to you. I have had experience doing OS installs before in high school, but that was with XP and on drives once they have been wiped. If the only way to do the install is wiping the drive clean, then that's not going to go over well because he has stuff he wants to keep on the 500 : /

One thing I noticed was that there is no master drive now, and the slave is the 80GB with ubuntu. The 500GB is under SATA1

If for some reason I'm beyond help then maybe I'll learn a thing or two here, haha.

Edit: here's more info while doing the W7 install
Disk 0 Partition 1: System Reserved  Total: 100 MB  Free: 70MB  Type:System
Disk 0 Partition 2:  Total: 465.7 GB  Free: 64.3GB  Type: Primary
Disk 1 Partition 1:  Total: 4.7 GB  Free: 0MB  Type:System
Disk 1 Partition 2:  Total: 69.9 GB  Free: 0MB  Type:Logical
(And then 2 externals)
I try to install on Disk 0 Partition 2 and it tells me "Setup was unable to create a new system partition or locate an existing system partition. See the Setup log files for more information."
But I can't find the setup log files

Thank you for reading and any help provided. It's greatly appreciated:)

---

### Post by ricardopresto on 2010-12-12
hi

how about booting into ubuntu, copying the stuff your mate wants to keep onto the 80gb drive, then formatting the 500gb drive and installing windows onto it?

ricardo

---

### Post by Kreios on 2010-12-12
thanks for the reply. Since there's only about 65 gigs left in the 500 then all of the stuff isn't going to fit. Maybe I can make another partition and install there...

---

### Post by argedion on 2010-12-12
> Disk 0 Partition 1: System Reserved Total: 100 MB Free: 70MB Type:System
Disk 0 Partition 2: Total: 465.7 GB Free: 64.3GB Type: Primary
Have you tried checking the drive to make sure its ok? It would also help if you were able to give the exact error message that W7 is giving you. Many of the guys in here are very good however they need specific information. My suggestion is to run testdisk and ensure that there is nothing wrong with the partitions themselves. If the computer has a bootable Ubuntu or atleast run the live cd and then run the bootscript from: [http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

this should help the local experts help you out with your problem

---

### Post by Kreios on 2010-12-12
Alright, well my friend is back from work and he has decided to cram all of his info into his other drives and format it. I'll update this with any news and do what you said if needed.

---


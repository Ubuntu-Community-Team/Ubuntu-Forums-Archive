---
title: "dual boot laptop"
date: 2011-08-18
forum: General Help
---

### Post by FishyMike on 2011-08-18
I am new to your forum so please be patient with my blunders if i make any. I have a Laptop that is dual booted with Win XP and openSuse. I am looking to change from openSuse to Ubuntu 11.4 but i am nervous about the re-installation from Suse to Unbuntu. I do not want to mess up the XP side.  I appreciate any Help I can get.

---

### Post by critin on 2011-08-19
Mike, since you're working with Windows, **Get advice on grub first in case it doesn't boot.  **
I** believe you'll need to redo MBR  on windows, so get an expert's advice.**
Do you remember how you handled it when you installed Suse?

I do this quite frequently and it's easy. (without windows though)   Use the live ubuntu cd  and go to Disk Utility under Admiinstration.  Click on your suse  partition and delete it.  Create a new partition in the same space. Close Disk Utility. Install ubuntu. Choose the empty space  to install to.  Be sure to take note of the partition number throughout  the delete and install.  I have never had an issue by doing it this way and I'm still a newbie.  I just let ubuntu configure the partition however it wants to.

critin

---

### Post by ubun2freak on 2011-08-19
@FishyMike: I'm not quite understand your idea. Dont you want to install all of those OS or just change from OpenSuse to Ubuntu. If you want to install all, just create a new partition and install ubuntu on it. Grub2 of Ubuntu will reliaze all of the installed OS, so you don't have to worry about boot-up operation.

have fun!

---

### Post by decrepit on 2011-08-19
As long as you know which partition windows is on, you won't have a problem.

If you no longer want suse, make sure ubuntu goes on suse's partition. You may have to reformat it or delete it first, I can't remember exactly how the ubuntu install goes.

I wouldn't worry about the MBR, ubuntu will install grub2, that will find your windows installation and give you the choice of booting it.

---


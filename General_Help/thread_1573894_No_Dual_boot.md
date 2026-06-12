---
title: "No Dual boot"
date: 2010-09-13
forum: General Help
---

### Post by jimbotz on 2010-09-13
Hi guys, i hope there is someone that can help me with this problem.
I was running win xp and decided to run a Dual boot system seeing as i had so much stuff on xp, i have installed Ubuntu 10.04 and it runs fine.
Problem is this, when i start my PC i am not seeing an option to Boot into windows, it goes into Ubuntu.
I can see my NTFS partition in "GParted" and it looks fine, i mounted the drive and all my files and folders are still present on the NTFS drive.
How can i get this sorted please as i do need to be able to still use xp.

Thanks for any help.

---

### Post by eriktheblu on 2010-09-13
In the terminal (or alt + F2 single command)
```
sudo update-grub
```

Lucid has a reputation for not detecting Windows on install, but this normally works.

---

### Post by jimbotz on 2010-09-14
> **eriktheblu said:**
> In the terminal (or alt + F2 single command)
```
sudo update-grub
```Lucid has a reputation for not detecting Windows on install, but this normally works.


Thank you [eriktheblu]("http://ubuntuforums.org/member.php?u=508854"), worked first time, came as as shock when i thought i had somehow got rid of my xp partition, i am sure this will be of great help to other newbies like myself.

---


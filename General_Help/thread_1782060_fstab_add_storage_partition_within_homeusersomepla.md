---
title: "fstab add storage partition within /home/user/someplace"
date: 2011-06-14
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2011-06-14
so i have this so far what do i do so i am able to store files on this partition without being root
```
UUID=51b2b46b-891c-490c-b8a6-a878595194b6 /home/chad/.VirtualBox/HardDisks ext4 defaults        0       4
```
what do i put where defaults is so i can saves files to that partition?
i get it now that is controlled with file permissions not within fstab
sudo chown -R chad:chad  /home/chad/.VirtualBox/HardDisks made it work

---


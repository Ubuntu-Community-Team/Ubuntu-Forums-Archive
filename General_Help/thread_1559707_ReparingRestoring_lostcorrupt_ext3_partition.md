---
title: "Reparing/Restoring lost/corrupt ext3 partition"
date: 2010-08-23
forum: General Help
---

### Post by phiyuku on 2010-08-23
I am not really a user of Linux so I have no idea how to go through with this. I had two hard drives connected to a router that acts somewhat as a NAS server (tomato firmware). I have thought that there should be no problem with converting to ext3 to increase speed dramatically from usually the 2MBps using NTFS to what I would get is around 6MBps when converted to ext3. Now about a day ago there was a short blackout. Checking it today I see that both hard drives have had all the data erased from it. It would show nothing not even lost&found. After e2fsck they both show lost&found but the data is still not there. I have looked into a program that uses Windows to recover data and a quick scan shows most if not all the data is there. Now that solution has two problems. 1) I don't have enough HDD space anywhere else to do it since writing into the same HDD would just overwrite the files. 2) The files are not named (112535.mpeg or something like that). I then tried to switch superblocks but that did nothing but change one the name of the drive to a previous name I gave it. Does anyone know what to do in this situation and why ext3 is so unreliable since whenever I have NTFS during a blackout/ computer just poofs for some reason, it would never happen.

---

### Post by phiyuku on 2010-08-24
Not sure if bumping is allowed but I really have no clue on what to do in this situation.

---


---
title: "Help Needed Moving WINES C:Drive to Separate Partition"
date: 2010-05-14
forum: General Help
---

### Post by cain071546 on 2010-05-14
I would like to move the C Drive To a separate partition
For I Am Running A Lil Low on Disc Space Having not Been Able To Either Look It Up Or Figure It Out My Self I Am Here
My Hard-drive is partitioned into 3 File Systems
The Partition I would Like To Have All My WINE Applications Installed in Is ext4 13Gigs How Would I Do This
                          Please Help

---

### Post by dcstar on 2010-05-14
> **cain071546 said:**
> I would like to move the C Drive To a separate partition
For I Am Running A Lil Low on Disc Space Having not Been Able To Either Look It Up Or Figure It Out My Self I Am Here
My Hard-drive is partitioned into 3 File Systems
The Partition I would Like To Have All My WINE Applications Installed in Is ext4 13Gigs How Would I Do This
                          Please Help
[LIST=1]
[*]Create a new folder to hold the data
[*]Copy the existing .wine contents to the new folder
[*]Rename the existing .wine folder
[*]Create a soft link from the new folder to replace the existing .wine folder
[*]Delete the renamed original .wine folder once you are certain everything actually works.
[/LIST]

---


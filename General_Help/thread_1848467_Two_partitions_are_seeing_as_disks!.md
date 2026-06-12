---
title: "Two partitions are seeing as disks!"
date: 2011-09-22
forum: General Help
---

### Post by acompay on 2011-09-22
[COLOR=black][FONT=Verdana][SIZE=3]Hello There,[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Verdana][SIZE=3]My PC has a hard drive (150GB) with two partitions of 75GB each. The OS is running in one partition and data are saved in the second partition. Now I would like to increase the size of the partition with the OS and I can't because Gparted and Acronis see two different disks. Why this is happening? What can I do to solve this problem?[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Verdana][SIZE=3]I would appreciate very much your help![/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Verdana][SIZE=3]Regards,[/SIZE][/FONT][/COLOR]

---

### Post by bodhi.zazen on 2011-09-22
First, please use the default text. [size=1][color=pink]Odd sized and miscolored text is annoying[/size][/color]

Second, please do not use the tips and tutorials section for technical assistance.

*Thread moved to **null**.*

Third you need to resize a partition when it is unmounted. This means using gparted from a live CD.

You almost certainly need to do this in two steps -> downsize your data partition -> apply changes -> increase the size of the OS partition.

Make sure the free space you make is adjacent to the partition you are upsizing.

---


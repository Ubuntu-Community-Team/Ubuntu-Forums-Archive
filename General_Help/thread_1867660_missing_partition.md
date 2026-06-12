---
title: "missing partition"
date: 2011-10-23
forum: General Help
---

### Post by ibbill on 2011-10-23
I have 4 partitions on my hard drive 1  18gb xp 1 76 gb Mint 1 spare listed as E drive with 110 gb free spare space and 1 with ubuntu 11.10 installed that I dont see I am now on the ubuntu 11.10 that I took the picture from.

Thanks for your help.

---

### Post by ibbill on 2011-10-23
Have taken a screenshot from the mint install also Still only see 3 partitions

---

### Post by Paddy Landau on 2011-10-23
It is not clear from your description what you are expecting to see.

Open *Disk Utility* and click on your hard drive. It will show you your partitions.

To make things easier in future, may I suggest that you label each partition (you can do that from Disk Utility: click a partition and select "Edit File System Label").

If you still have concerns, post back with a screenshot of your Disk Utility (or, if you prefer, the output of [FONT=Fixedsys]sudo parted --list[/FONT] and [FONT=Fixedsys]sudo blkid[/FONT]).

---

### Post by westie457 on 2011-10-23
Hi, could you do either of these two things please. Open a terminal and post the output of ```
sudo fdisk -l
``` (that is a lowercase L) or boot into XP go to the MMC > Storage > Drives and post a screenshot of your partitions.

Thank you.

---

### Post by ibbill on 2011-10-23
thanks guys here is a snapshot of the disk and the shot from the terminal

---

### Post by lynrock on 2011-10-23
There are three extra partitions plus the one that your are on (File System) = four. Which is correct.

---

### Post by ibbill on 2011-10-23
Okay guys thanks pardon the DOH. Will also change the names so I have a slight idea of what I am doing . Thanks again.

---

### Post by Paddy Landau on 2011-10-23
Glad it's solved. Partitions can be a little confusing if you don't keep on top of them!

---

### Post by ibbill on 2011-10-23
Yes thank you ever so much. Tip about renaming them was very helpful lot easier to see where I am lol.

Have to change them on both Mint and Ubuntu thanks again for the tip.

---

### Post by Paddy Landau on 2011-10-23
> **ibbill said:**
> Have to change them on both Mint and Ubuntu...
The label belongs to the partition, not to the system that names it. Whether you name the partitions from Ubuntu, Mint or even Windows (assuming Windows could rename ext4 partitions, which it cannot) makes no difference. If you take out the hard drive and put it in a Mac machine, the labels will still be there.

---


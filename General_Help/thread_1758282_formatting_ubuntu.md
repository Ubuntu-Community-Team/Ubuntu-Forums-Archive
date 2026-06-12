---
title: "formatting ubuntu"
date: 2011-05-14
forum: General Help
---

### Post by magodiafano on 2011-05-14
Hello... I would like to format my ubuntu because I did several mistakes (my audio does not work anymore)! I have dual boot with windows vista. Is there a way to format only the partion of ubuntu??

---

### Post by Mark Phelps on 2011-05-14
You could remove the Ubuntu partition using the Vista Disk Management utility.

Or ...

You could boot using the Ubuntu LiveCD, open Partition Editor, and reformat the partition that way.

---

### Post by sanderd17 on 2011-05-14
It's not called fromatting, it's called "doing a fresh install". Just in case you google it, you will find more. One part of "doing a fresh install" is the formatting part.

To answer your question: YES, You can format a single partition.

Some questions for you:

Do you want to keep your files on Linux? If no, there is no problem

If yes: did you create a separate /home partition on installation? If you did, there is no problem, you can just format the right ubuntu partition and the files will be kept.

If you did't (or if you don't know how to create a separate /home partiton), you will lose the files on your linux installation, so copy them somwhere else before you begin.

---

### Post by Hedgehog1 on 2011-05-14
If you have your data in a separate '/home' partition you can reinstall 11.04 over your 10.10 '/' partition and be sure to not format the '/home' partition:

First, define your '/' (root) partition:

[IMG]http://img31.imageshack.us/img31/7520/04allocdrivespace2.png[/IMG]

[IMG]http://img130.imageshack.us/img130/9673/05allocdrivespace3.png[/IMG]

Then define your '/home' partition:

**[SIZE="4"]IF YOU ARE DOING A RE-INSTALL, DO NOT FORMAT THIS PARTITION![/SIZE]**

[IMG]http://img202.imageshack.us/img202/6828/07allocdrivespace5.png[/IMG]

This separates your documents and 'stuff' from the system files and 'stuff' in the '/' partition.

***The Hedge***

:KS

p.s. To learn how to move your '/home' into it's own partition: **_[SeparateHomePartition]("http://www.psychocats.net/ubuntu/separatehome")_**

---

### Post by Ryuzaky on 2011-06-23
I got another Question regarding about partions wich is the best format to install Ubuntu Bare with me im new to Ubuntu any info woul be very helpfull :)

---

### Post by sanderd17 on 2011-06-23
It's not good practice to open an older thread, you should normally start a new one unless you have the same very specific bug (which rarely happens, even if you have the same symptoms).

Apart from that, what do you mean with "format"?

The best way to install ubuntu for the first time is to use the guided way, just select to install it next to your windows and let the Ubuntu installer determine the space needed.

---

### Post by life in color on 2011-06-23
I would suggest booting GParted LiveCD then simply deleting your ubuntu partition and taking the new free space and allocating it back to your windows partition(ntfs).

---


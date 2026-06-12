---
title: "Question about installing Ubuntu with Wubi."
date: 2012-01-06
forum: General Help
---

### Post by jason99 on 2012-01-06
Hello,
I would like to install Ubuntu 11.10 with Wubi onto a partition with data (pictures, music, etc.) on it. My question is: if I install Ubuntu onto that partition, will it erase the data on it already?
Thanks in advance!
-Jason A.

---

### Post by Basher101 on 2012-01-06
wubi will not erase anything at all. the wubi install is like any other windows program, it just takes some hard drive space. the only difference is you can boot into it...

because a ubuntu wubi install is treated as a normal windows program, you can simply delete it with system settings -> uninstall software

the wubi installation is for people who want to try out ubuntu but do not want to mess with partitions or make live CD/USB boots all the time.


regards

---

### Post by jason99 on 2012-01-06
Thank you!

---

### Post by Basher101 on 2012-01-06
you may mark your thread as [SOLVED] with the forum tools at the top

enjoy your time with Ubuntu! just be patient about things that do not work out of the box and you will find your way and not regret doing so :popcorn:

---

### Post by jason99 on 2012-01-06
Before I marked it solved, I have one more question: why are there multiple installation sizes available, like 9 GB and 17 GB?
Thank you again!

---

### Post by Basher101 on 2012-01-06
your wubi install will create a virtual partition for ubuntu where it can be installed to. Ubuntu (or linux in general) uses the ext4 filesystem which is not compatible with the NTFS filesystem windows uses. So you must set the size of the virtual ext4 partition where ubuntu is going to be installed to (note: a fresh install without updates takes 4 GB).


p.s. ext4 is alot more advanced than the NTFS windows uses, it must NEVER be defragmented. EVER. (love that, saves a ton of time)

---

### Post by jason99 on 2012-01-06
Thank you, again!

So I just started the Wubi installer, but when I did, a dialog box popped up and it says: "There is no disk in the drive. Please insert one into the drive.
\Device\Harddisk2\DR28" or similar!
At the top it says: "pyrun.exe No Disk"
Why?

---

### Post by lisati on 2012-01-06
> **jason99 said:**
> Thank you, again!

So I just started the Wubi installer, but when I did, a dialog box popped up and it says: "There is no disk in the drive. Please insert one into the drive.
\Device\Harddisk2\DR28" or similar!
At the top it says: "pyrun.exe No Disk"
Why?
This is a known issue. The usual workaround is to "safely remove" card readers and other USB devices that you won't need during the installation. See [https://bugs.launchpad.net/ubuntu/+bug/365881](https://bugs.launchpad.net/ubuntu/+bug/365881) for more information.

---

### Post by Basher101 on 2012-01-06
do you have enough space available?

note: i have no experience on wubi installs as i have never done any (i jumped right to the full install), so i can't give you much help on some errors you might encounter.

edit: thanks lisati for answering on my behalf (i could not have known the answer to fix it :D)

---

### Post by jason99 on 2012-01-06
Thank you everyone! Marking as [SOLVED].

---


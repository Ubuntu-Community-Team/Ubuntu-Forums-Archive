---
title: "System shows folder as empty"
date: 2010-06-25
forum: General Help
---

### Post by whatsnext on 2010-06-25
Hi everyone and thanks in advance for your support.

I have a compaq laptop with a hard disk separated in three partitions:

Partition 1: Ubuntu 9.04
Partition 2: Windows XP
Partition 3: Data

I usually work 95% of my time with Ubuntu, but store all my data in the data partition, so the information is always available no matter if I work under Windows or Ubuntu.

The system has been working perfectly well for several months, but a couple of weeks ago I detected that some subfolders are shown as empty, but I know that there are several files on them (mostly pdf files document-scanned). When I use windows, all the files are shown correctly. In other folders, the system shows some files, but not all of them. (again mostly PDFs are not shown).

My Ubuntu system is fully updated. The data partition is in NTFS format. Linux is EXT4. Windows is NTFS again.

I would appreciate to know if any of you guys have detected a similar problem and if so, how to solve it.

Regards from Spain, and thanks again.

---

### Post by burton247 on 2010-06-25
I haven't come across this before. The obvious and I don't think this is it but are the files hidden? 

The only real thing I can suggest is navigating to the folder through the terminal and trying to view the contents from there. Could be your FM playing up

---

### Post by whatsnext on 2010-06-29
Hi Burton, Thanks for your reply.

Obviously not; I have assured myself several times that the files are not hidden.

It doesn't happen with all the subfolders, only with this particular one, although I think that in other subfolders some files (specially PDF ones) are not shown on its totality.

When I access to the data from windows, everything is there.

I guess it must be something malfunctioning within the file system (NTFS) which is not native to linux. Perhaps FAT should have been used for this data partition.

I will follow your advice and try to access from terminal window just to try. Will keep you posted.

BTW, could you please indicate what FM stands for?

Thanks again and Brgds

---

### Post by burton247 on 2010-06-29
Stands for file manager. If you can see the files via the terminal then it is likely to be that which is playing up

---

### Post by whatsnext on 2010-06-29
Hi again Burton, sorry for disturbing you.

I have checked the folder using the terminal window, and it displays correctly all the files inside the folder, so you were right on this issue: it must be something wrong within the File Manager.

Any idea on how to solve this problem?

Thanks in advance for your contribution.

brgds

---

### Post by burton247 on 2010-06-29
Not overly unfortunately. I had a hunt and found this though, might be helpful

[http://ubuntuforums.org/showthread.php?t=1318218]("http://ubuntuforums.org/showthread.php?t=1318218")

---

### Post by whatsnext on 2010-07-14
Hi Burton, sorry for late reply. I want to tell you that I have been able to solve the problem.

Apparently the problem was caused by some sectors of the disk that the system marked as unusable or something like that. I discovered this when I restarted the computer and ordered an scandisk. This program discovered this and I allowed the program to repair it.

When I restarted the computer, everything was there again.

Its strange what has happened, because to the best of my understanding, if the sectors/clusters were wrong, these files should not be shown nor in windows, neither in the terminal window in Ubuntu, but ........

Thanks again for your support. Matter closed successfully.

---


---
title: "PGarted displays erroneous  error info"
date: 2012-10-13
forum: General Help
---

### Post by Cavsfan on 2012-10-13
This has been bothering me for nearly the past week. GParted shows my windows 7 partition to have a bad sector. 
I have ran CHKDSK many times in windows and Ubuntu still shows the error.

Then today I find that when the windows drive is mounted in Ubuntu everything is good.

This is what I have been seeing in Ubuntu: 

[[IMG]http://ompldr.org/tZnZjMg[/IMG]]("http://ompldr.org/vZnZjMg")

This is what I see when the drive is mounted in Ubuntu: 

[[img]http://ompldr.org/tZnZjNQ[/img]](http://ompldr.org/vZnZjNQ)

Windows says the partition is fine and so does Ubuntu if it is mounted.
CHKDSK is a very slow time consuming disk check/fix windows program and it appears I have been wasting a lot of time. ](*,)


It is refreshing to know that there is absolutely nothing wrong with my drive but, Cheese Wiz! 
What is going on here? This is the same in Quantal, Precise and Lucid.

---

### Post by conradin on 2012-10-14
Windows will also (typicaly) never tell you when your disk is failing. 
I suspect chkdsk only looks at your filesystem, and doesn't report disk errors. A bad sector is a hardware problem. You filesystem can be fine however with numerous failed sectors. having multiple failed sectors is a good hint to replace your drive. For bad sectors I think chkdsk just limits access by the Filesystem to those sectors.

---

### Post by Cavsfan on 2012-10-14
> **conradin said:**
> Windows will also (typicaly) never tell you when your disk is failing. 
I suspect chkdsk only looks at your filesystem, and doesn't report disk errors. A bad sector is a hardware problem. You filesystem can be fine however with numerous failed sectors. having multiple failed sectors is a good hint to replace your drive. For bad sectors I think chkdsk just limits access by the Filesystem to those sectors.

Thanks for the reply. One thing chkdsk does is identify bad sectors and attempts to move the data to good sectors.
It makes note of the bad sectors so they will not be used again, thus "repairing" the drive.
CHKDSK is supposed to be run at regular intervals to make sure your hard drive remains in good condition.
It actually goes through 5 stages while checking the hard drive.

[LIST]
[*]Stage 1: Checking files – Chkdsk examine the volume’s master file table (MFT) and checks for consistency.
[*]Stage 2: Checking indexes (directories) – Chkdsk checks each  directory for consistency. It also verifies that the files represented  in the directory match the files described in the MFT. In addition, it  verifies that there are no cycles in the directory tree.
[*]Stage 3: Checking Security Descriptors – Chkdsk checks the NTFS  security descriptor stream and related data structures, verifies the  security descriptor for each file, and cleans-up unused security  descriptors. This phase is run only if the Chkdsk/f option is specified.
[*]Stage 4: Verify File Data (only run when /R or /B is specified) –  Chkdsk reads the data of every file to see if there are any bad clusters  in the file data. Any file with bad clusters is repaired and all bad  clusters are added to the NTFS bad cluster list.
[*]Stage 5: Verify Free Space (only run when /R or /B is specified) –  Chkdsk verifies every free cluster on the volume to see if there are any  bad clusters. All bad clusters are added to the NTFS bad cluster list.
[/LIST]
So, in Windows everything is fine just like in Ubuntu when my Windows partition is mounted.
I also have Defraggler installed in Windows 7 and it checks the hard drive and reports that it is in "good" condition.
I can even benchmark it with Defraggler and that also reports the drive is good.

So, the drive is good but, for some reason GParted says it is has a bad sector when unmounted.

I tend to trust Windows to tell me the condition of it's partition more than another OS.

---

### Post by conradin on 2012-10-14
Imagine drilling a hole in your hardrive then running chkdsk. Chkdsk finds and isolates the hole in your disk and isolates it from the filesystem. 
Disk utility tells you about the hole. 
The repair isnt a repair, the sector is still bad after you run chkdsk, the filesystems is just repaired to deal with the hole (failed sector).

Failed sector counts, among other things remain relevant to your system even if your FS is repair around them. I wouldnt say the notification is erroneous.

[http://en.wikipedia.org/wiki/S.M.A.R.T](http://en.wikipedia.org/wiki/S.M.A.R.T).

---

### Post by Cavsfan on 2012-10-15
> **conradin said:**
> Imagine drilling a hole in your hardrive then running chkdsk. Chkdsk finds and isolates the hole in your disk and isolates it from the filesystem. 
Disk utility tells you about the hole. 
The repair isnt a repair, the sector is still bad after you run chkdsk, the filesystems is just repaired to deal with the hole (failed sector).

Failed sector counts, among other things remain relevant to your system even if your FS is repair around them. I wouldnt say the notification is erroneous.

[http://en.wikipedia.org/wiki/S.M.A.R.T](http://en.wikipedia.org/wiki/S.M.A.R.T).

I understand exactly what you are saying but, how do you explain that GParted reports the windows drive has an error when it's not mounted.
Yet, finds no such error when it is mounted?

---


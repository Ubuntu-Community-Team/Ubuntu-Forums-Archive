---
title: "Installing 10.04 problem"
date: 2010-08-03
forum: General Help
---

### Post by saidbakr on 2010-08-03
Hi,
Everytime I try to install 10.04 I got the following error in the same place of the installation:

The Installer Encountered Unrecoverable Error. 

It tells me that it will start new live session to fix the problem.

The Error always occures during creating  the file system exactly at 5% of the progress.

I thought that it may be due to a mistake in setting partitions. I choose delete and install over all the hard disk but the error is the same.

Is there any solution for this problem?

By the way, I thought it sue to an error in the cd, I downloaded it again and I verified its md5 hash and it is correct.

Please look at the attached screenshot.

---

### Post by saidbakr on 2010-08-03
This is another attachment screenshot for the error message.

---

### Post by Smart Viking on 2010-08-03
Hi, in the live CD, open "gparted", and format the whole thing as ext4.

_IF_ that works, then open the installer again, and when it comes to the partitioning thing, chose "manual blabla" or whatever it is called, then mount the big partition in "/"(root) and do NOT format it, leave it as it is. I don't know it will work but it was while creating the filesystem that the installer failed, now it will not have to do so since you did it in gparted. I hope this helps. :)

---

### Post by saidbakr on 2010-08-04
Hi, 
I have done as you told me and the installer is turned off after the following screen shot is rendered.
So removing confilicting operating system files leads now to the problem.

By the way I partitioned the disk as follows - it is 160 GB -
/boot 50 MB
/        40000 MB
/home  115500 MB
/swap ~4000 MB

---

### Post by saidbakr on 2010-08-04
I just need to know, Does it real bug or not.  tested it on two machines and the same problem is identical.

---

### Post by Smart Viking on 2010-08-04
In two machines? That sounds like a faulty CD to me, i would suggest burning a new one. :)

---

### Post by saidbakr on 2010-08-04
Well,
I have made 5 CDs and I downloaded two iso images for 10.04. However, one of those CDs was not able to load the install, another one could not able to run live CD correctly, while other one could not able to setup Ubuntu under MS Windows XP.

However, md5 hash for both downloaded iso files is correct and equals its value on Ubuntu website.

I wonder, how could the CD able to run and installing Ubuntu under Windows - the current CD I use - and loading the installation while its being faulty?!

The question now: How could I able to check the CD to know if it is faulty or not?

---

### Post by saidbakr on 2010-08-05
Thank you, Smart Viking, very much. Yes it is a problem with my CD Writer Drive it writes CDs bad. I used another CD to burn the iso and then I used Check Desc featue found in the starting options of the Ubuntu CD and it said no errors then the installation is completed perfectly.

---


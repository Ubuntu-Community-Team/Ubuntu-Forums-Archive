---
title: "Why Is The Size Of My Home Folder Limited?"
date: 2011-05-11
forum: General Help
---

### Post by kernelles on 2011-05-11
It seems Ubuntu 11.04 has limited how big my Home folder can be. Since it's "full"  even though there is plenty of space on my drive, my computer won't even send emails because it says there isn't enough space on the drive. Can someone please help me? 

Attached is a screen shot of my disk usage. 

Thanks,
Les.

---

### Post by wojox on 2011-05-11
You only allocated a 11.7 GB partition for ubuntu.

---

### Post by jtfolden on 2011-05-11
How are your partitions laid out? Is Home a partition of its own?

---

### Post by kernelles on 2011-05-11
> **wojox said:**
> You only allocated a 11.7 GB partition for ubuntu.

Am I misreading the screen shot, then? I'm interpreting it to mean that  there is 328GB allocated for Ubuntu, and only 11.7GB is being used so  far. It's a 1TB hard drive, and 328GB is about how much I remember allocating for Ubuntu on install. Did I do something wrong?

---

### Post by kernelles on 2011-05-11
> **jtfolden said:**
> How are your partitions laid out? Is Home a partition of its own?

Not unless Ubuntu does this by default on install.

---

### Post by wojox on 2011-05-11
> **kernelles said:**
> Am I misreading the screen shot, then? I'm interpreting it to mean that  there is 328GB allocated for Ubuntu, and only 11.7GB is being used so  far. It's a 1TB hard drive, and 328GB is about how much I remember allocating for Ubuntu on install. Did I do something wrong?

No you are right I read it wrong. Do you have a seperate home like jtfolden asked?

---

### Post by kernelles on 2011-05-11
> **wojox said:**
> No you are right I read it wrong. Do you have a seperate home like jtfolden asked?

No, not unless Ubuntu did this by default on install. Does it?

---

### Post by arsenic23 on 2011-05-11
Type 'df' (without the quotes) into a terminal and paste the results.

---

### Post by kernelles on 2011-05-11
I'm wondering if this has any thing to do with the way I installed it. 

I installed Natty over Meerkat on an already dual-booted machine (Win 7 & Ubuntu), so I used the manual/advanced partitioner in the installer. I edited the only ext4 partition, told it to reformat it and chose the mount point of "/" and install there.....was this the wrong thing to do?

---

### Post by kernelles on 2011-05-11
> **arsenic23 said:**
> Type 'df' (without the quotes) into a terminal and paste the results.

Here you go:

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda5            344238024  11990324 314761352   4% /
none                   4119696       720   4118976   1% /dev
none                   4128928      4968   4123960   1% /dev/shm
none                   4128928        96   4128832   1% /var/run
none                   4128928         0   4128928   0% /var/lock

---

### Post by SavageWolf on 2011-05-11
Uh, the disk usage thing only anylises space used.

The "size" col means how much space that folder takes up, not the size of the drive, while the "usage" is what percentage of the parent folder is in this folder.

How counter-intuitive.

---

### Post by grahammechanical on 2011-05-11
I have been comparing my system with your system. In my case the home is said to be 88.5% full with 32.4Gb but at the top I am told that 37GB is used with 171.4 GB available.

Now if I click Scan Home I get a different picture. All the folders under my user name are listed and the size of the data in them.

I know that my /home partition is about 208 GB. So, 37 GB and 171 GB adds up about right.

I think that disc utility is showing you the data sizes of the system folders in the home folder. It is not measuring the size of the home partition. It certainly is not including the folders under the user name. You have to scan home to measure that. The 100% figure in both scans means that it has fully scanned that area (I think).

My guess is that your do not have a separate home partition and the partition being used is indeed nearly full because it is too small.

You need to run GParted from a live CD and see what that program shows about your partitions. A screenshot would help.

Regards.

---

### Post by ajgreeny on 2011-05-11
> **SavageWolf said:**
> Uh, the disk usage thing only anylises space used.

The "size" col means how much space that folder takes up, not the size of the drive, while the "usage" is what percentage of the parent folder is in this folder.

How counter-intuitive.
It is something that catches a lot of people out, and I agree makes it quite unintelligible to the casual user.  Why on earth it works that way, I have no idea, but I do wish it would change and give the proper answer that most users expect.

It does, however, add another good reason for looking at the cli output from such simple commands as ```
df -h
```which gives the same output as the command you used, but more understandable with MB instead of rather meaningless numbers.  The cli wins again.

---

### Post by mcduck on 2011-05-11
> **SavageWolf said:**
> Uh, the disk usage thing only anylises space used.

The "size" col means how much space that folder takes up, not the size of the drive, while the "usage" is what percentage of the parent folder is in this folder.

How counter-intuitive.

+1 to this. It's analyzing the disk usage of your files and directories, not the amount of used/available space on a certain filesystem.

So the directory you have selected will always be 100%, and all it's subdirectories and their contents will be displayed as percentages relative to that directory.

It's a great tool for analyzing *where* your disk space is being used and *what's* using it, but *not* for checking the available space on your filesystems. You can kind of use it for that too, if you limit it's scan to only one filesystem at a time and then view the root of that filesystem. There are much better tools for viewing filesystem usage, though for example the System Monitor will do that for you (although I prefer a simple "df -h" in a terminal).

I actually think the Disk Usage analyzer is a great tool, and you *can* figure out what it does if you just play around it a bit (you should notice how the percentage values of any directory's contents always add up to 100%), but I definitely agree that the purpose of the tool (and how to use it) could be made clearer to new users.

---

### Post by wildmanne39 on 2011-05-11
Hi, I had the same problem with mine when I upgraded, to natty it did not go over the top of the old ubuntu like it was suppose to and it was the first time that I did not set my partitions manually so it put the 2 ubuntus side by side and I ran out of space in my home folder. Also it does not create a separate home folder it is all on the root. I had to use gparted to resize and move my partition and it made it not bootable, so I had to reinstall grub but it was a very tricky process. Long story short with natty it is better to do a fresh install.:D

---

### Post by kernelles on 2011-05-12
Thanks for the help, everyone. I realize I misunderstood the way the Disk Usage Analyzer reports info. However, this still makes me wonder why my computer was telling me it didn't have enough memory to even send an email until I cleared some files off?

---


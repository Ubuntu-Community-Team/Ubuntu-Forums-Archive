---
title: "Installed and lost Files (pictures, music) and previous OS"
date: 2010-05-20
forum: General Help
---

### Post by Murenai on 2010-05-20
Hello everyone,
New to ubuntu and having issues...
I installed Ubuntu 10.04 using the Side by Side option (Vista).
Ubuntu works fine but at the start I have no option to witch OS to use, jumps directly to Ubuntu.
I cannot find my files that I had and used from Vista and according to Ubuntu my HD is almost empty when I had only about 50 or 60 GB available.
What happened the other 190 GB of files, music, pictures....
Should I panic?
Read about someone experiencing similar issues at start up, have now installed the updates and problem persists...

thanks for your help

---

### Post by 3Miro on 2010-05-20
1. When the system is starting, press and hold Shif. You should be given a menu with at leas two options for Ubuntu (normal and fail safe) and hopefully Vista.

2. If there is no Vista, then you can go to the terminal (Apps -> Accessories -> Terminal) and type:
```
sudo fdisk -l
```
This will ask you for your password and then it will display the current structure of your hard drive.

Here is mine:
```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2432    19535008+  83  Linux
/dev/sda2            2433       30401   224660962    5  Extended
/dev/sda5            2433        3161     5855661   82  Linux swap / Solaris
/dev/sda6            3162        9240    48829536   83  Linux
/dev/sda7            9241       30401   169975701   83  Linux

```

I am running pure Linux so that is all that I get in the System column (I have 4 Linux partitions and the Extended one is kind of a fake one). You should get at least one "HPFS/NTFS" or just "NTFS".

---

### Post by Murenai on 2010-05-20
Hello 3Miro,

Thanks for your quick reply.

After pressing shift upon start up I get 6 options:
 2 Ubuntu with linux (each with a generic and recovery mode, so 4) 
+ 
2 memory tests
But no Vista

This is what the terminal is showing:

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29273   235129856   83  Linux
/dev/sda2           29273       30402     9066497    5  Extended
/dev/sda5           29273       30402     9066496   82  Linux swap / Solaris

No   HPFS/NTFS" or just "NTFS

As you would guess, I don't really mind about Vista (would be nice to recover all but my main concern as all the files, I am sure and would like to believe that when Ubuntu got installed it did not format the HD, that would have taken much more time, my guess is that my files/documents are in the HD but the root to them is missing
any ideas?

---

### Post by silkworm2.5 on 2010-05-20
What did you actually do to install side by side? Partitioning or Wubi?

---

### Post by techunit on 2010-05-20
It looks as though you ended up wiping out windows entirely...

---

### Post by techunit on 2010-05-20
Um I don't know if there is a way to recover such data, but this is why you back up all your data first.

---

### Post by Murenai on 2010-05-21
> **silkworm2.5 said:**
> What did you actually do to install side by side? Partitioning or Wubi?

I believe Partitioning..

Vista had my 250gb HD (laptop) partitioned in 2 (C: + D: ) and from what I can see, this vista partitioning became only one.

But if widows is wiped out, then normally Ubuntu would have been installed in the same space as windows, right?
Thus the files that were in the D drive should be "untouched"...

If it helps I de-fragmented the HD before installing

---

### Post by 3Miro on 2010-05-21
Here is what I know about data recovery from a reformatted HDD.

1. Stop using your machine immediately and turn it off. By turning it off, people usually mean unplug it off. However, in this case I don't think it will do much good.

2. Boot from a CD and find a tutorial with some HDD recovery tool to try and access deleted files.

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

READ CAREFULLY.

When Linux formats (also modern day versions of Windows), they simply rewrite the partition table and the file reference table. SO data is still technically there, it is just that the system doesn't know how to get to it. Some files may be at least partially recoverable.

---

### Post by Murenai on 2010-05-22
Big thanks 3Miro,

With your guidance and a lot of help from a friend I got 90% of my files back!

Now I am only using Ubuntu! it rules!

Big thanks again!

---


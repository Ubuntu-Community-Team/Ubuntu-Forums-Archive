---
title: "Input/output error when accesing a directory"
date: 2010-10-25
forum: General Help
---

### Post by tjoff on 2010-10-25
Hi 

I have a directory "foo" on a NTFS partition of my hard drive, which i created a couple of days ago. 
After creation it worked fine and i put some files in it, but the day after i get the following error:

me@mymachine:/media/disk1$ ls -l foo
ls: cannot access foo: Input/output error

me@mymachine:/media/disk1$ ls -l
ls: cannot access foo: Input/output error
total 101
d????????? ? ?     ?         ?                ? foo
(+ a succesful listing of other files and directories)

I get the Input/output error no matter what i try to do to the directory (rm, mv, cd, etc.), and no matter which privileges i have.

I read some threads suggesting that it is a hardware problem. I tried running ntfsfix on the partition:

me@mymachine:~$ sudo ntfsfix /dev/sda3
Mounting volume... OK
Processing of $MFT and $MFTMirr completed successfully.
NTFS volume version is 3.1.
NTFS partition /dev/sda3 was processed successfully.

I have also run the short and the long SMART test from the disk utility, resulting in the overall assessment: Disk is healthy.

It would be nice to know how to recover the data in the directory, but i have backup so that part is not crucial. I could also reformat the whole drive to ext4, which I eventually would have done in any case. Or i could just ignore the defective folder which does not harm anyone.
However if this problem is the first warning of a failing drive, I would rather get a new drive now, before some more important data suddenly disappear.

My question is now, what course of action i should take. 
Is there any other diagnostics that i could try? Is it a soft- or hardware related issue. Should I begin looking for a new hard drive?

---

### Post by blueturtl on 2010-10-25
That most definitely seems like a bad hard drive.

Of course a hardware problem elsewhere could also cause data/file system corruption. Do you have reason to suspect it could be anything else? Upgraded your CPU or RAM lately?

---

### Post by tjoff on 2010-10-25
Thanks for the reply.
Nope, no hardware changes. I've been running Hardy to Karmic on unchanged hardware without problems of this kind before.
I guess I should look into changing the disk. However it would be nice to be able to verify that the hardware is to blame.

---

### Post by 3rdalbum on 2010-10-25
> **tjoff said:**
> Thanks for the reply.
Nope, no hardware changes. I've been running Hardy to Karmic on unchanged hardware without problems of this kind before.
I guess I should look into changing the disk. However it would be nice to be able to verify that the hardware is to blame.

You answered your own question. Try a Karmic.live CD and see if the problem still occurs.

---

### Post by tjoff on 2010-10-26
Thank you for taking the time to answer me.

Regarding booting from a live-CD:

I tried it, the problem persists. 
I still wonder however, what I have proved by booting from the live CD. 
How should I be able to distinguish between a corrupted filesystem (in which case the problem can be solved by reformatting the drive), and a physically failing hard drive (in which case the solution is to exchange the drive)?

I was hoping to be able to make some kind of diagnostics for the hard drive, which could give me a more verbose error message than "Input/output error", and indicate the what causes the error.
I did all the tests from the disk utility tool, and none indicate any problems.

A definite proof or disproof that the hardware is failing would, apart from assuring myself that it is necessary to change the drive, come in handy as there is still a valid guarantee on the computer.

---

### Post by tjoff on 2010-10-29
I tried to boot with windows xp, and chkdsk or whatever it is called found the errors and deleted the corrupted directory. 
In ubuntu i no longer have any indication of the problem. I guess it was a software problem after all, and that ntfsfix was not able to fix the ntfs.

---

### Post by jaya28inside on 2010-11-25
huhuhu,
me also encountered the same thing as yours, tjoff.

the case in me is that,
my ftp mounted directory seems can not accept 
some files after cp operation... Geeez... :(

---


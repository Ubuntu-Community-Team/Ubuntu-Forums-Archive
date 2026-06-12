---
title: "Urgent help"
date: 2012-02-24
forum: General Help
---

### Post by holytree on 2012-02-24
I have a wubi installation of ubuntu 11.10 running alongside windows xp

I now have a  fully corrupted windows xp

So how can  i access all the local disk d local disk e local disk f 
from ubuntu

Its really important as i have important files on it

PLEASE HELP URGENTLY!!!

Regards,
HolyTree

---

### Post by roelforg on 2012-02-24
First of all; XP isn't fully corrupted.
If it was, Ubuntu (via wubi) wouldn't boot either.

---

### Post by roelforg on 2012-02-24
Also; i'm not sure if the Linux people (me included) here will be able to help you with a windows problem.

---

### Post by wyliecoyoteuk on 2012-02-24
This might help:

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by holytree on 2012-02-25
Nope it dint help i want to use the local disks not the c drive :(

---

### Post by kurja on 2012-02-25
I'm not entirely sure exactly what is the problem or what you're trying to do, but to access those disks, launch Disk Utility (under system > administration), then click on the disk(s) you want to access, choose "mount", and they should have become visible in your "places" menu. Please do post back with your results.

---

### Post by raja.genupula on 2012-02-25
insert a Ubuntu Live CD and run into Live Desktop mode , access and take back up all your important files from there to you USB flash .

my suggestion is better to install Ubuntu in separate partition. so you could have Dual boot system and if even Xp corrupted you can get access from Ubuntu . 

hope that helps .

---

### Post by holytree on 2012-02-25
Uh a little help thanks everyone for attending to my post..

As I got to disk utility there is this local disk which says is NOT clean  
my windows xp is slower than a snail

can i clean the drive from ubuntu if i can how?

Regards,
Holytree

---

### Post by holytree on 2012-02-25
@Raja - can i access files from windows also??

---

### Post by kurja on 2012-02-25
> **holytree said:**
> Uh a little help thanks everyone for attending to my post..

As I got to disk utility there is this local disk which says is NOT clean  
my windows xp is slower than a snail

can i clean the drive from ubuntu if i can how?

Regards,
Holytree

Now that you're in in disk utility, note the problem disk's "address" - /dev/sda1, for an example. Unmount the volume, open console and run ```
sudo fsck /dev/sda1
```replacing sda1 with the address of your disk. See how it goes, and do post back.

---

### Post by kurja on 2012-02-25
> **holytree said:**
> @Raja - can i access files from windows also??

You can access everything on the disk.

---

### Post by holytree on 2012-02-26
Oh hello! thanks and i will try that im currently downloading the live cd

I have found out which drive has the problem it is the F: drive i will format it.
And i will get back to all of you with the results..!!

---

### Post by bcbc on 2012-02-26
If the F: 'drive' is not clean you need to run "chkdsk /f" on it. Assuming it's an NTFS drive.

You can't do that from Ubuntu. You need to run it from Windows or from a Windows repair command prompt.

Formatting should get around the problem but you'll lose all your data.

---


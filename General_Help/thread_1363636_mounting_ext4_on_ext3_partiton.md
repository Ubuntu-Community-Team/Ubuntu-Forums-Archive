---
title: "mounting ext4 on ext3 partiton"
date: 2009-12-24
forum: General Help
---

### Post by 10ghost on 2009-12-24
hi all,
I tried mounting my ext4 partion on my ext3 partition but thus gives me an error whenever i attempt this.
I am sure i am not the only one having this problem.
When i went to google to search for such a problem . The recommendation was to convert the ext3 filesystem to ext4.
I want to know if  there is any other way  of solving this problem?
And if one convert to an ext4 filesystem what are the implications?

---

### Post by taurus on 2009-12-24
Not sure if I understand exactly what you want to do?  You want to mount an ext4 filesystem as an ext3?

---

### Post by 10ghost on 2009-12-24
> You want to mount an ext4 filesystem as an ext3? 
Not exactly. I want to mount the ext4 filesystem on an ext3 filesystem.
But if it is possible to mount an ext4 as ext3 on an ext3 i would not mind if you can tell me how.
But from what i have read this is not posible. This is still subjective until proven otherwise.

---

### Post by taurus on 2009-12-24
Any reason you want to mount ext4 filesystem as an ext3 filesystem?  The machine that you are using doesn't support ext4 filesystem?

---

### Post by 10ghost on 2009-12-24
I have 2 versions of ubuntu running on my machine. The jaunty uses ext4 and the 8.04 uses ext3. They  both run fine. I can mount the ext3 on the ext4 but the reverse has not been possible.
So the case of my machine not been able support ext4 is not true.

So i guess there is sth else wrong.

---

### Post by Finalfantasykid on 2009-12-24
I'm guessing he already has an ext3 partition with data on it, but he uses an ext4 partition for the OS.
Its like when you mount a Windows Partition(ie: NTFS).

I don't know how to fix the problem, but it might help knowing what sort of error messages you are getting, or maybe try mounting it in the terminal as that could give you some extra information.

EDIT:  Ok reading your above post, I think I know what the problem is.  Ext4 was not released when 8.04 was around.  It wasn't until 9.04 I think that ext4 was recognizable to the OS.  So the problem is in your version of Ubuntu that you are using to access the ext4 partition.  Maybe there are some extra packages that you could download that would allow for r/w of an ext4 partition using 8.04.

---

### Post by 10ghost on 2009-12-24
First i would really like to apologize to Taurus about what i said about my system supporting ext4.
The error message is actually
```
The volume uses ext4 file system which is not supported by your system
```
This is error it gives on attempting to mount this ext4 file system.
Hope this would help to solve my problem.

---

### Post by falconindy on 2009-12-24
> **Finalfantasykid said:**
> Maybe there are some extra packages that you could download that would allow for r/w of an ext4 partition using 8.04.
OP would need up to update his kernel in order to mount the partition.

---

### Post by bodhi.zazen on 2009-12-24
> **falconindy said:**
> OP would need up to update his kernel in order to mount the partition.


This ^^

@10ghost :

No need to apologize, it is just that the way you phrased your question does not make sense.

A partition is prepared for use via "mounting" it. You mount it at a location, say /media/data or wherever you choose.

See : [How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

The problem you have is Ubuntu 8.04 does not have the capability to mount ext4

You could mount an ext4 partition if you compiled a custom kernel, but it may not function properly =)

IMO you are best off making a shared data partition, make it ext3, and then you can mount it in either OS.

---


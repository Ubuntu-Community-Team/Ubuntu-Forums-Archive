---
title: "Ubuntu 10.4 64 Bit Growth Partition Size Error"
date: 2010-05-09
forum: General Help
---

### Post by Tanner2007 on 2010-05-09
So this is the problem

My ubuntu partition had 25 gb of space, and only had little bit of 500 mb free space

so i booted of a 9.04 ubuntu cd and used gparted and moved about 30 - 40 gb of free space from my windows partition to ubuntu

everything was fine until it got to the check file system stage of the process and gave me an error, and now matter how many times I do this, I even tried e2fsck -f check in terminal as error said to run this first,

still nothing

so the error is even tho i had 500 mb of free space and moved about 30 - 40 gb of free space, it says that new space is now filled up so i STILL only have a little over 500mb free

so I know restarting the pc cant add about 40 gb of space taken, and I havae had this before and doing the check file system in gparted always worked, untill now, so guys what do i do?

---

### Post by James78 on 2010-05-09
Where are you running the command? It is not recommended to run the command on a root fs that is mounted. Especially because if it does come across errors on the mounted fs, and you fix them, then it will likely corrupt the entire drive.

---

### Post by Tanner2007 on 2010-05-09
> **James78 said:**
> Where are you running the command? It is not recommended to run the command on a root fs that is mounted. Especially because if it does come across errors on the mounted fs, and you fix them, then it will likely corrupt the entire drive.

I ran commands off live cd's terminal and typed in right partition

---

### Post by James78 on 2010-05-09
Alright, just making sure.

---

### Post by Tanner2007 on 2010-05-09
> **James78 said:**
> Alright, just making sure. Anyways, next thing would most likely be to reinstall grub. I assume you're using Grub2 (default for Karmic and Lucid)?

How're your hard drives configured as far as master and slave go? For example, I have /dev/sda as Windows, and /dev/sdb as Linux.

It is likely that Grub may have overwritten something on the MBR or Windows boot partition that it shouldn't have, but this can most likely be easily fixed.

I hope you have a Windows Vista install disk, because the MBR utilities on it will be useful to restore any Windows MBR/Boot damage, which might be the case here why it's not booting.
I don't think its grub, ubuntu loads up fine, it just miss reading the used and free space, which before this has happen a check system in gpart always worked, now gpart gives me error message

---

### Post by James78 on 2010-05-09
Excuse me, I posted the message in the wrong topic. -.- I'm not sure what you can do if the checking utility won't see the problem, but have you tried using chkdsk for your Windows partition?

The only reason I can think of it not catching the problem is that either the parameters to e2fschk were wrong/incorrect, e.g. not in the form of /dev/sda1 or just the wrong drive/number.

---

### Post by Tanner2007 on 2010-05-09
No problem bro, but maybe this can help people with what I am trying to say 

error
[[IMG=http://img689.imageshack.us/img689/5123/screenshot1ve.th.png][/IMG]](http://img689.imageshack.us/i/screenshot1ve.png/)


and in the save details htm file

```

GParted 0.4.3

Libparted 1.8.8
Check and repair file system (ext4) on /dev/sda5  00:00:18    ( ERROR )
     	
calibrate /dev/sda5  00:00:00    ( SUCCESS )
     	
path: /dev/sda5
start: 330071553
end: 470463524
size: 140391972 (66.94 GiB)
check file system on /dev/sda5 for errors and (if possible) fix them  00:00:18    ( SUCCESS )
     	
e2fsck -f -y -v /dev/sda5
     	
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

280347 inodes used (13.50%)
869 non-contiguous files (0.3%)
492 non-contiguous directories (0.2%)
# of inodes with ind/dind/tind blocks: 0/0/0
Extent depth histogram: 242299/491
3574998 blocks used (43.07%)
0 bad blocks
1 large file

207141 regular files
28040 directories
68 character device files
26 block device files
0 fifos
620 links
45059 symbolic links (37447 fast symbolic links)
4 sockets
--------
280958 files
e2fsck 1.41.4 (27-Jan-2009)
grow file system to fill the partition  00:00:00    ( ERROR )
     	
resize2fs /dev/sda5
     	
resize2fs 1.41.4 (27-Jan-2009)
Please run 'e2fsck -f /dev/sda5' first.


```

but i do run 
e2fsck -f /dev/sda5

and all i get is
 ```

ubuntu@ubuntu:~$ sudo e2fsck -f /dev/sda5
e2fsck 1.41.4 (27-Jan-2009)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/sda5: 280347/2076704 files (0.5% non-contiguous), 3574998/8299572 blocks
ubuntu@ubuntu:~$ 



```

so what do i do?

---

### Post by James78 on 2010-05-09
Well, running resize2fs -f /dev/sda5 instead will force it to resize, instead of going out with the error, although that isn't recommended, it may cause system damage, or it may completely fix your issue.

To me it feels like the only option here. And it might fix your problem for good!

---

### Post by Tanner2007 on 2010-05-10
> **James78 said:**
> Well, running resize2fs -f /dev/sda5 instead will force it to resize, instead of going out with the error, although that isn't recommended, it may cause system damage, or it may completely fix your issue.

To me it feels like the only option here. And it might fix your problem for good!

I believe I tried that with no success

---

### Post by James78 on 2010-05-10
Hmm, then I just ran out of options.. Anyone else have a clue?

You see, the problem is occurring because:
resize2fs won't work, which should've worked after using "resize2fs -f /dev/sda5"

So you see it's sorta a pickle now...

---

### Post by Tanner2007 on 2010-05-10
> **James78 said:**
> Hmm, then I just ran out of options.. Anyone else have a clue?

You see, the problem is occurring because:
resize2fs won't work, which should've worked after using "resize2fs -f /dev/sda5"

So you see it's sorta a pickle now...

Well maybe if I move another 5 gb it will work? hmm

---


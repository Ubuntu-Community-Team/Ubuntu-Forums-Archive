---
title: "Where do i find good instructions for gddrescue"
date: 2011-11-15
forum: General Help
---

### Post by MissBaksel on 2011-11-15
[SIZE=2]Hi,

2 weeks ago, my external hard drive fell down while I was copying something. 
Now I can't open the data. First I couldn't get acces to the drive but after googling and typing sum commands in the terminal I can open the hard drive and see the files but there's nothing in them if you open the files.

So I googled further and installed gddrescue because this is supposed to be better than ddrescue. Now I have the program on my OS. but I don't know how to use it. I'm new in ubuntu and I'm not used to work with terminals. 

So my question is: Does anybody know where I can find a good manual for gddrescue?[/SIZE]

[SIZE=2]Thanks[/SIZE]:cool:

---

### Post by jjex22 on 2011-11-15
I've not used it myself, but it should come with one - try typing

man gddrescue

That should bring up the list of options and a guide on how to use.

---

### Post by oldfred on 2011-11-15
Some links.
gddrescue, Scalpel, magic rescue, photorec, foremost, sleuthkit & others
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/)

[http://www.gnu.org/software/ddrescue/ddrescue.html](http://www.gnu.org/software/ddrescue/ddrescue.html)

But if you cannot see anything, there may not be anything to recover. Drives can only take so much damage, and often that is not much.

---

### Post by MissBaksel on 2011-11-16
[SIZE=2]Typing man gddrescue doesn't do anything but if I type man ddrescue, I get a list of instructions. First I'm going to look up wath the difference is between these two programs because I think they might work with the same instructions.  I'm probably going to find this in oldfred's pages;)

Thanks for the tips guys[/SIZE]

---

### Post by WasMeHere on 2011-11-16
Hi John,

I have used ddrescue and I can recommend it :-)

Read also ```
info ddrescue
```which contains a well written manual as well as a mini-tutorial!

Have fun finding out
Olle

---

### Post by MissBaksel on 2011-11-17
Hello,

I also discovered the info command but it still is hard for me to work with ddrescue:D.
Finally I am starting to understand what commands I have to put into the terminal. I also read somewhere that you need 3 drives to recover your data, one for the image(raw data), one for the new data, and your old damaged hard drive. It should be possible to do this with 2 or am I mistaking?
If I get results, I will post them in this topic.

btw; 
I had to change my name (John Tampon) into another name because it might be to offensive. Just wanted to say that I'm not a perv:). My new name means I'm ugly in Dutch

---

### Post by WasMeHere on 2011-11-17
> **MissBaksel said:**
> ... I also read somewhere that you need 3 drives to recover your data, one for the image(raw data), one for the new data, and your old damaged hard drive. It should be possible to do this with 2 or am I mistaking? ...

You need
1. the (failing) drive to rescue data from
2. one drive to boot from (separate from the drive to rescue from).

If you make an image, you could put it on the boot drive. But often you boot from some small removable media, a CD or USB drive, too small to keep an image. So you need

3. one drive to write the rescued data to.

It is easier to manage and reuse data if you [try to] clone your failing drive to a new drive of the same size or larger.

(4) Furthermore, if you boot from a CD and want to save your log file persistently, you need another drive (for example a USB drive).

I suggest that you work according to Example 1 below. First you must identify your drives. I suggest that you use the following commands
```
sudo fdisk -lu
df
``` to identify which is your failing drive and clone-to-be. It is very important that you get the letters right, otherwise you will overwrite your data and they will be lost forever!!!

If you boot from an Ubuntu live disk, the first disk is almost always named [FONT="Courier New"]/dev/sda[/FONT] and the second one [FONT="Courier New"]/dev/sdb[/FONT]. But you can not be sure that the first one in the bad one, mount and check with df if necessary, then unmount, because during the rescue operation the disks must ***not*** be mounted. 
--- info ddrescue ---
```
Example 1: Rescue a whole disc with two ext2 partitions in /dev/hda to
/dev/hdb
Note: you do not need to partition /dev/hdb beforehand.

     ddrescue -n /dev/hda /dev/hdb logfile
     ddrescue -dr3 /dev/hda /dev/hdb logfile
     fdisk /dev/hdb
     e2fsck -v -f /dev/hdb1
     e2fsck -v -f /dev/hdb2

```
You have to be patient because these operations take several hours.

Finally, it is better that you ask now, than guess and ask afterwards ;-)

---

### Post by MissBaksel on 2011-11-17
Ok thanks for the advice.
I'm using the second example on the manual.
```
Example 2: Rescue an ext2 partition in /dev/hda2 to /dev/hdb2.
Note: you need to create the hdb2 partition with fdisk first. hdb2
should be of appropiate type and size.

     ddrescue -f -n /dev/hda2 /dev/hdb2 logfile
     ddrescue -d -f -r3 /dev/hda2 /dev/hdb2 logfile
     e2fsck -v -f /dev/hdb2
     mount -t ext2 -o ro /dev/hdb2 /mnt
       (read rescued files from /mnt)

```But I have a NTFS partition so I am going to replace the ext2 line by NTFS. Is this correct?

When I read your post. I paused the command to unmount my disks because I wasn't sure. 
These are my results so far:
```

john@john-desktop:~$ sudo ddrescue -d -f -r3 /dev/sdc /dev/sdb logfile


Press Ctrl-C to interrupt
Initial status (read from logfile)
rescued:     12288 B,  errsize:      1 TB,  errors:       1
Current status
rescued:     12288 B,  errsize:      1 TB,  current rate:        0 B/s
   ipos:   906314 kB,   errors:       1,    average rate:        0 B/s
   opos:   906314 kB,     time from last successful read:       1 h
^Clitting failed blocks...
Interrupted by user
john@john-desktop:~$ sudo umount /dev/sdc
[sudo] password for john: 
umount: /dev/sdc: niet aangekoppeld
john@john-desktop:~$ sudo umount /dev/sdb
umount: /dev/sdb: niet aangekoppeld
john@john-desktop:~$ sudo ddrescue -d -f -r3 /dev/sdc /dev/sdb logfile


Press Ctrl-C to interrupt
Initial status (read from logfile)
rescued:     12288 B,  errsize:      1 TB,  errors:       1
Current status
rescued:     12288 B,  errsize:      1 TB,  current rate:        0 B/s
   ipos:     1878 MB,   errors:       1,    average rate:        0 B/s
   opos:     1878 MB,     time from last successful read:     9.4 m
Splitting failed blocks...
```Does this seem OK?
Thanks;)

---

### Post by oldfred on 2011-11-17
Linux uses fsck or e2fsck for file checking ext type partitions. 

If it is NTFS you have to use chkdsk from a Windows drive or repairCD or USB. There are only a few minor repairs to NTFS that can be done from Linux.

---

### Post by WasMeHere on 2011-11-18
> **MissBaksel said:**
> ...
john@john-desktop:~$ sudo ddrescue -d -f -r3 /dev/sd[COLOR="Red"]c[/COLOR] /dev/sd[COLOR="Red"]b[/COLOR] logfile
...
If you are sure about /dev/sd[COLOR="Red"]c[/COLOR] and /dev/sd[COLOR="Red"]b[/COLOR] you can go along with the ddrescue sessions (the two command lines). If it was wrong you have already destroyed the beginning of a drive because you started it, so I really wish you got it right.

And as already stated by Oldfred, NTFS partitions are repaired by ***chkdsk*** in Windows. So after the two ddrescue sessions, boot into Windows, or move the cloned copy to a Windows computer and run chkdsk to repair it software-wise.

Good luck :-)
Olle

---

### Post by dcstar on 2011-11-18
When using ddrescue on a drive that has significant damage, I recommend the following options:

[LIST=1]
[*]-r 2 (maximum 2 retries, otherwise it takes too long)
[*]-d (Don't let the OS try and access the drive, it can add too much time to any bad block retries)
[*]-c 8 (The 128 sector default can complicate and slow things)
[*]-v (The more info the better)
[*]-n (If the disk is really bad, this won't waste as much time on the unreadable blocks)
[/LIST]
```
sudo ddrescue -r 2 -d -c 8 -v -n infile outfile [logfile]
```

---

### Post by MissBaksel on 2011-11-18
@olle: Yes I'm sure of the input and output files. I always check them, sometimes they change, if I had them unplugged or something.
```
john@john-desktop:~$ sudo ddrescue -d -f -r3 /dev/sd[COLOR=Red]c[/COLOR] /dev/sd[COLOR=Red]b[/COLOR] logfile
```This does mean that I want to copy the data from sdc to sdb?

@dcstar: I tried your code but then he said my output file allready exists and it was not a regular file. I deleted the logfile on my ubuntu partition and then tried again with a force command (-f) included. This took 4seconds and he didn'r rescue anything.

My hope is starting to break down because I tried it for a while now without results and I know you don't get a lot of attempts with damaged hard drives.](*,):p

---

### Post by WasMeHere on 2011-11-18
> **MissBaksel said:**
> @olle: Yes I'm sure of the input and output files. I always check them, sometimes they change, if I had them unplugged or something.
```
john@john-desktop:~$ sudo ddrescue -d -f -r3 /dev/sd[COLOR=Red]c[/COLOR] /dev/sd[COLOR=Red]b[/COLOR] logfile
```This does mean that I want to copy the data from sdc to sdb?

Yes, go ahead and good luck
Olle

---

### Post by dcstar on 2011-11-19
.

---


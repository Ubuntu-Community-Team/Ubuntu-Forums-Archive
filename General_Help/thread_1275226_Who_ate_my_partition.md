---
title: "Who ate my partition??"
date: 2009-09-25
forum: General Help
---

### Post by BarisBlaq on 2009-09-25
Hi!

I'd been using Ubuntu from live cd 9.04 for a while now, and although I'm still pretty noob to linux, I decided to take the step today to install Ubuntu all over my laptop =))

I have a 300 gb hd, so i created 3 partitions - 50 gb for /, 245 gb for an ext3 partition that i plan on using for storage (persistent between upgrades), and a 5gb swap

I succeded (following instructions on various posts) to auto mount the extra storage partition, and making it read/writeable.

The problem is, when I check this partition, even though nothing is on it yet, it seem 16 gb is already used and only 229 gb is available.

The only thing that is there s the empty Lost&Found folder. Is this taking up a portion of the partiiton by defualt? Is there a way to manually limit its size?

On second note, when I check the partiion through gparted, it shows 5 gb used and 240 gb available. But when I check it through nautilius, its 16 used and 229 available like i said above.

I did a clean install, creating the whole partition from scratch, fyi.

Any ideas on what is using up 16 gb of my blank partition?

And if its lost&found, any tips on how to downsize it?

Thanks in advance!

---

### Post by scragar on 2009-09-25
Try running du over the directory it's mounted to:
```
du -h /mount/path
```
The -h flag is for human readable(it will print 12M instead of 12045973 which is much easier to read IMO).

---

### Post by BarisBlaq on 2009-09-25
Thanks for quick response!

> baris@BlackBox:~$ du -h /Stuff

12K    /Stuff/Admin
16K    /Stuff/lost+found
32K    /Stuff


I'm not sure what that means, though =/

---

### Post by scragar on 2009-09-25
It means you shouldn't be using any space at all, unless...
```
sudo du -hs /Stuff/*
```
I wonder if it is the lost+found folder(I use sudo because lost+found is owned by root, it's normally used to recover files on the hard drive, they're owned by root because otherwise anyone might own such files(and of course they get given daft names because there's no name associated with them)).

---

### Post by BarisBlaq on 2009-09-25
Thanks again, just to clarify since english is not my forte.. Should I run the command you wrote to try fix it?

My system is clean install so I can reinstall with no loss of data if something goes wrong, but just didnt understand if you were asking me to do it or suggesting an alternate way to mount the partition (I did it with some /etc/fstab addition)

---

### Post by scragar on 2009-09-25
That command just takes a closer look at what's on the partition(and hopefully should show where all the space you're missing is being used), I still can't see what would be using the space, but it has to be something or you wouldn't have this problem at all.

---

### Post by BarisBlaq on 2009-09-25
Oh ok.. I was irked by the sudo, before reading your edit =)

> baris@BlackBox:~$ sudo du -hs /Stuff/*
[sudo] password for baris: 
12K    /Stuff/Admin
16K    /Stuff/lost+found
baris@BlackBox:~$ 


Again, thanks for taking the time to deal with me, mate

---

### Post by BarisBlaq on 2009-09-25
I did a re-install, and still the same..

In nautilus, it seems 16 gb of the 245 gb partition is used..

In gparted, 4 gb is used and 241 is free..

And yet the partition has nothing on it..

I don't know whic is correct, and I hope none is, since its a blank partition..

Any help is appreciated, thanks a bunch

---

### Post by t0p on 2009-09-25
Check out [this page]("https://help.ubuntu.com/community/RecoverLostDiskSpace").  Its focus is how recover disk space when it's full, but some of it should apply to your problem.

Also use the Disk Usage Analyzer (**Applications > Accessories >Disk Usage Analyzer**).  It might show what's using the space.

---

### Post by egalvan on 2009-09-25
Under Linux, various file systems "set-aside" a specific amount of disk space for the journal,
and to have extra for when the partition is filling up.

This is usually around 5% of the total allocated space.

Take into account other over-head,
and 16 out of 226 isn't that bad...

about 8%.

I once read an article on reducing the amount of "set-aside" space for a partition that was to be used *strictly* for storage,
but I can't recall it at this moment.
Anyone else recall this?

ErnestG

---

### Post by apmcd47 on 2009-09-25
> **BarisBlaq said:**
> Thanks for quick response!

```
baris@BlackBox:~$ du -h /Stuff

12K /Stuff/Admin
16K /Stuff/lost+found
32K /Stuff 
```

I'm not sure what that means, though =/

My guess is that you have some bad sectors on that partition and they have been "safely gathered" in the lost+found folder. Is there anything there when you do:
```
sudo ls -l /Stuff/lost+found
```

Andrew

---

### Post by egalvan on 2009-09-25
> **apmcd47 said:**
> My guess is that you have some bad sectors on that partition
 and they have been "safely gathered" in the lost+found folder.
Andrew

Bad sectors are not "safely gathered" in the lost+found folder.
"Lost Sectors" , "Lost Links" and other such "lost" data that cannot be linked to valid locations (logical validity) are moved there.

Bad sectors are re-allocated (re-mapped) by the drive's electronics, and are replaced by sectors from a pool of spares.
When the pool runs dry, the drive starts giving "bad sector errors".

---

### Post by louieb on 2009-09-25
> **egalvan said:**
> Under Linux, various file systems "set-aside" a specific amount of disk...
This is usually around 5% of the total allocated space.


Default is 5% reserved. When installing using the text based alternate CD there is that option to change the reserve %. (Don't know about the live installer)  Anyway it can be adjusted using tune2fs.

With larger drives 5% can be a significant amount of space. Don't know how far it can be reduced and still be safe.

---

### Post by BarisBlaq on 2009-09-25
Thanks for the responses so far..

The lost&found folder is not the problem, because i sudo deletede it, and the 16 gb is still shown as used..

The 5% reserved journal seems logical, since my "used" space is roughly that much (16 out of 245, around 6,5%)

I tried the manpage of tune2fs, but I'm a bit hesitant about the options.. This partition is not normally mounted to the "filesystem", i meant it to be a data storage partition so didn't mount it anywhere at installation. I then added it as automount to /etc/fstab

However, in the tune2fs options, I cant seem to find any option to designate a particular partition. I'm guesing the "-J size=" wpuld be used to limit the kournal size, but wouldnt that affect the journal size of the Ubuntu filesystem, and not the other partition I'm having problems with?

---

### Post by louieb on 2009-09-25
Man pages are a language of there own - you'll get use to it. It would be nice if there were an example section. 

```
tune2fs -m3  /dev/sda4 
```> 
       -m reserved-blocks-percentage
              Set the percentage of the filesystem which may only be allocated
              by privileged processes.   Reserving some number  of  filesystem
              blocks for use by privileged processes is done to avoid filesys&#8208;
              tem fragmentation, and to allow system  daemons,  such  as  sys&#8208;
              logd( 8 ,  to continue to function correctly after non-privileged
              processes are prevented from writing to  the  filesystem.   Nor&#8208;
              mally, the default percentage of reserved blocks is 5%.



---

### Post by egalvan on 2009-09-25
> **BarisBlaq said:**
> 
The lost&found folder is not the problem, because i sudo deletede it, and the 16 gb is still shown as used..

No, lost&found is not the problem...

> The 5% reserved journal seems logical, since my "used" space is roughly that much (16 out of 245, around 6,5%)

Yepper, that's close enough...

> I tried the manpage of tune2fs, but I'm a bit hesitant about the options..
 **This partition is not normally mounted** to the "filesystem", i meant it to be a data storage partition so didn't mount it anywhere at installation.
 I then added it as automount to /etc/fstab

many partition operations require that the partition not be mounted.
but mounted or not, all hard drives and partitions have designations.
such as:
sdx
UUID
LABEL


> However, in the tune2fs options, I cant seem to find any option to designate a particular partition.
 I'm guessing the "-J size=" wpuld be used to limit the journal size, but wouldn't that affect the journal size of the Ubuntu filesystem, and not the other partition I'm having problems with?


Limiting the journal size is not the way to go. Leaving it at the default is much safer.


use the code that  **louieb** gave as an example...
you want to limit the reserved blocks....
these reserved blocks are used by the system for 'system' type operations.

De-fragmentation is the only real concern, and is the reason I leave this at the default 5%.

All-in-all, it's a small price to pay for the safety features of the Linux journaling file system.

---

### Post by BarisBlaq on 2009-09-26
Thank you louieb and egelvan!

Using tune2fs with -m3 like you suggested indeed free up some of those hidden gbs.
=)

But as egelvan suggested, it is a small price, so i set it back up to -m5. Since its a big drive (for me at least) I didnt really need those gb badly, but was just curious what was using them.

Thanks again to all those responded, folks!

---


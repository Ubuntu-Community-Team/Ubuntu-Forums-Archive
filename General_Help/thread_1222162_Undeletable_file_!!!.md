---
title: "Undeletable file !!!"
date: 2009-07-24
forum: General Help
---

### Post by fasti on 2009-07-24
hello everybody,

I have a large file, 1.9 GB, on an NTFS partition,
that I have been UNABLE TO DELETE.

doing:
# sudo rm -f 072707.wmv

gives:
# rm: cannot remove `072707.wmv': Input/output error


what should i do?

---

### Post by bacil on 2009-07-24
try first

```
 fuser 072707.wmv
```

then kill process that is hanging on that file and try deleting it again

---

### Post by fasti on 2009-07-24
That didn't work.

(but thanx).

I was guessing some program might be using the file (like a movie player)
but after restarting the computer, the file refuses to be deleted.

(doing:
 #  fuser 072707.wmv
 didn't print any users (any proccesses).
 and I still get:
 # rm: cannot remove `072707.wmv': Input/output error ).

Please help...

---

### Post by blazemore on 2009-07-24
If you really HAVE to delete it, try booting from a LiveCD and deleting it from there.

---

### Post by aesis05401 on 2009-07-24
> **fasti said:**
> That didn't work.

(but thanx).

I was guessing some program might be using the file (like a movie player)
but after restarting the computer, the file refuses to be deleted.

(doing:
 #  fuser 072707.wmv
 didn't print any users (any proccesses).
 and I still get:
 # rm: cannot remove `072707.wmv': Input/output error ).

Please help...

Are you able to 'stat' or 'file' the file in question?

---

### Post by fasti on 2009-07-24
> 
Are you able to 'stat' or 'file' the file in question? 


Yes.

doing:
# file 072707.wmv
gives:
# 072707.wmv: data

and doing:
# stat xxxxxx.wmv
gives:
#  File: `xxxxx.wmv'
#  Size: 2068648625	Blocks: 4040336    IO Block: 4096   regular file
# Device: 816h/2070d	Inode: 168         Links: 1
# Access: (0777/-rwxrwxrwx)  Uid: (    0/    root)   Gid: (    0/    root)
# Access: 2009-07-24 21:22:24.000000000 +0300
# Modify: 2009-07-22 11:59:05.000000000 +0300
# Change: 2009-07-23 01:31:05.000000000 +0300

(I think these are ordinary print outs for a file).

Why should booting from a live CD help? If it was a permission issue,
doing "sudo rm" as I did would have helped, wouldn't it?

Any other suggestions?

---

### Post by wojox on 2009-07-24
Download the NTFS configuration tool

[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

You need the ntfs-3g driver

---

### Post by aesis05401 on 2009-07-24
> **fasti said:**
> *snip* ... Why should booting from a live CD help? If it was a permission issue,
doing "sudo rm" as I did would have helped, wouldn't it?

Any other suggestions?

This is a file living in a standard folder, right?  

The person who posted that a livecd would help is referring to situations  where you are dealing with a mount issue.  This is not a mounted image is it?  That would produce this error, and could be resolved with a umount command or by booting into a livecd environment where all the local mounts are inactive.

---

### Post by michy99 on 2009-07-24
I don't know if a file on a NTFS partition can have attributes, but just for the heck of it, what does this show?```
lsattr 072707.wmv
```

---

### Post by fasti on 2009-07-24
1) wojox
> You need the ntfs-3g driver 
I think the partition is already loaded with ntfs-3g, because
in /etc/fstab the partition is mounted this way:
> /dev/sdb6 /media/Partition3 ntfs-3g rw,locale=en_US.utf8,uid=1000 0 0
and I use this partition all the time (downloading files, deleting them).

Could it be that I don't actually have the ntfs driver even though all the other files on that partition allow deletion?

2) aesis05401
> This is a file living in a standard folder, right?
it's in the root of the partition, without folders.
And I'm not sure what you mean by "mounted image", but it's just a wmv file,
like many others I download and delete daily. nothing special. (presumably..).

3) michy99
doing:
# lsattr 072707.wmv

gives:
# lsattr: Inappropriate ioctl for device While reading flags on 072707.wmv

---

### Post by fasti on 2009-07-24
btw

I umounted and mounted the partition, and it didn't resolve the problem.

---

### Post by wojox on 2009-07-24
Have you tried moving it and deleting:

```
mv -f 072707.wmv begone.wmv
```

---

### Post by fasti on 2009-07-24
same outcome-
# sudo rm -f 072707.wmv
# rm: cannot remove `072707.wmv': Input/output error
# sudo mv -f 072707.wmv death.wmv
# mv: cannot move `072707.wmv' to `death.wmv': Input/output error

---

### Post by Cl0ud9 on 2009-07-24
Not sure if this will help, but I would try something like:

```

sudo echo 0 > 072707.wmv
sudo rm -f 072707.wmv

```

---

### Post by aesis05401 on 2009-07-24
> **fasti said:**
> same outcome-
# sudo rm -f 072707.wmv
# rm: cannot remove `072707.wmv': Input/output error
# sudo mv -f 072707.wmv death.wmv
# mv: cannot move `072707.wmv' to `death.wmv': Input/output error

Alright, then you need to run a utility to check the filesystem unfortunately.

---

### Post by wojox on 2009-07-24
File system Check:

```
e2fsck /dev/sdb6
```

---

### Post by niteshifter on 2009-07-24
> **wojox said:**
> File system Check:

```
e2fsck /dev/sdb6
```

Ah... no. OP's problem is not with a extended 2 or 3 file system, it's with a NTFS file system.

His problem is there is an error reading that particular file. Possibly can be fixed by ntfsfix, part of the package ntfsprogs. More likely fix is let Windows' chkdsk do it's check and repair on the partition.

---

### Post by aesis05401 on 2009-07-24
*snip* n/m

---

### Post by fasti on 2009-07-25
I umounted the partition and did:
# sudo ntfsfix /dev/sdb6

The result was:
> Mounting volume... OK
Processing of $MFT and $MFTMirr completed successfully.
NTFS volume version is 3.1.
NTFS partition /dev/sdb6 was processed successfully.

I mounted the partition again, and THERE IS A CHANGE.
for:
# file 072707.wmv
I get:
> 072707.wmv: **empty**

???

Don't tell me the drive doesn't recognize the free space now....!

I am not satisfied at all(!), because the free space on my partition
DID NOT increase by 1.9 GB (the original size of this annoying file).

Doing "ls -la" shows THE FILE IS STILL THERE, and reports it's of 0 length,
even though I didn't get my free space back.
And still, I  get for:
> sudo rm -f SJ_072707.wmv
the same answer:
> rm: cannot remove `072707.wmv': Input/output error

And I notice another anomaly in "ls -la" printout:
> -rwxrwxrwx 1 root root  241945145 2009-05-19 01:55 prisonbreaks03e04.wmv
-rwxrwxrwx 1 root root          0 2009-07-25 13:20 072707.wmv
-rwxrwxrwx 1 root root 1559072154 2008-09-27 09:39 080507.wmv
-????????? ? ?    ?             ?                ? Aidn2.wmv
-rwxrwxrwx 1 root root  259937421 2009-05-19 01:52 prisonbreaks03e05.wmv
drwxrwxrwx 1 root root      65536 2009-07-25 21:00 Azureus
-rwxrwxrwx 1 root root    1574459 2009-04-26 02:13 Azureus_Stats.xml
drwxrwxrwx 1 root root          0 2009-06-10 19:38 backup ff3.5 stuff

Do you see the line with the (???????) question marks?

---

### Post by aesis05401 on 2009-07-25
Ok, calm down.  Files have two parts - the name and the actual data.  Your results have confirmed that we are on the right track.  

Give me a minute to go through my bookmarks and I will be back with some advice. 

Anyone else know the resolution right off the bat?

---

### Post by aesis05401 on 2009-07-25
Alright, we are one step further... 

I hit up some docs and found that ntfsfix does not complete the ntfs recovery process, only fixes the file system enough that windows can run chkdsk on the next boot to finish fixing the filesystem.  

This is consistent with what we are seeing.  Before ntfsfix you could not get some attributes from the file, now you can see it is empty - so the actual data portion of the file has now been fixed to some degree.

Now we need to remove the entry that is telling the filesystem that the space is still occupied.

Do you still have a bootable windows install?  If so, booting into that OS should cause chkdsk to pop up.  If you allow that process to complete you should regain the ability to remove the file.

If not... then post back and we will think of something else.

---

### Post by fasti on 2009-07-25
Firstly, I would like to thank you all, and aesis05401 in particular, for helping me in trying to fix this problem.

Secondly,
about 2 years ago (maybe more) I switched to Ubuntu, and have been
exceedingly content with it, especially in comparison with inferior OS such
as all those microsoft products (windows).

So, I am proud to say-
I DO NOT have a "windows" installation on my UBUNTU pc. :)

(upper case not intended to indicate indignation). :)


please, pleeeease don't tell me I was wrong to tell everybody
that I need-not anything made by microsoft... :)
(I know, the fault is mine in keeping the drives in NTFS file systems
instead of switching to ext3 / ext 4...). Let this be a lesson to you all..!

---

### Post by aesis05401 on 2009-07-25
Hello fasti.  

I would like to say thank you for bringing your issue to the forums.. when we figure out how to deal with this it will be very useful to many people. 

I have found a couple different things that may help us here.  First, what command are you using to view the available space on the partition?  Certain disk tools pull info from tables that can become stale if corruption occurs because information was added or removed outside the normal process.  If this is the case we can fix your issue easily. 

Another approach is a little more radical.  

You can run your NTFS partition through ntfsclone to attempt a further repair.  Doing this will force each ntfs file entry to be verified against the data sectors in the process of cloning. 

The ntfsclone documentation says it can correct types of NTFS corruption, but I have never used it for this purpose.  I would suggest backing up important files before doing this. 

Please post back.

---

### Post by aesis05401 on 2009-07-25
Hmm. and another thought - the question marks in the 'ls -la' you posted indicate a permission problem for that line item.  

You get '?' when you have insufficient privilege to stat a file.  If you ran the ls -la with 'sudo' and still saw ??? we would know something more.

---

### Post by fasti on 2009-07-27
(excuse me for not posting yesterday, I was stuck late at work...)

> Hmm. and another thought - the question marks in the 'ls -la' you posted indicate a permission problem for that line item.

You get '?' when you have insufficient privilege to stat a file. If you ran the ls -la with 'sudo' and still saw ??? we would know something more.

I actually found something that has to do with permissions-
In the Partition I have a folder, lets call it FatherFolder,
and in it I have another folder, lets call it ChildFolder.
(this isn't a school question, the names are just better for explaining).

What I found is that I can make new folders in the Partition,
and I can make new folders in the ChildFolder, but I CAN'T make new folders
in the FatherFolder !
(this applies to all actions that require permissions, like creating and
 deleting files...).

I get this message:
> Error creating directory: Input/output error
which to me sounds a lot like "rm: cannot remove `072707.wmv': Input/output error".

So, how do I fix all these permission problems?

aesis05401 -ntfsclone sounds dangerous to me, and I don't have enough 
free storage to backup the whole partition. (If I did, I wouldn't be trying
 so hard to delete that 1.9 GB file...).

BTW - the file I was asking you guys about, isn't in these two folders
that I mentioned, it's on the root of the partition.

---


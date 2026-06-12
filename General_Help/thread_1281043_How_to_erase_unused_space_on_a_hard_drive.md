---
title: "How to erase unused space on a hard drive?"
date: 2009-10-02
forum: General Help
---

### Post by solwic on 2009-10-02
I'm trying to figure out how to basically shred all the unused space on my hard drive, like what the "shred" command does to individual files.  

I know of a couple ways to do this for Windows, but none for Linux.  

Anybody point me in the right direction?

Much appreciated!

---

### Post by wojox on 2009-10-02
Just found it last week, but haven't had a chance to try it fully yet

```
sudo apt-get install secure-delete
```

[http://www.techthrob.com/2009/03/02/howto-delete-files-permanently-and-securely-in-linux/](http://www.techthrob.com/2009/03/02/howto-delete-files-permanently-and-securely-in-linux/)

---

### Post by solwic on 2009-10-02
> **wojox said:**
> Just found it last week, but haven't had a chance to try it fully yet

```
sudo apt-get install secure-delete
```

[http://www.techthrob.com/2009/03/02/howto-delete-files-permanently-and-securely-in-linux/](http://www.techthrob.com/2009/03/02/howto-delete-files-permanently-and-securely-in-linux/)

Thanks.  Will try it now.  Anybody know of any others?

---

### Post by renkinjutsu on 2009-10-02
I'm just posting because i'm curious..
What do you mean by shredding unused space? .. like the unpartitioned space that shows up in gparted? or like... free space that hasn't been used yet? Then wouldn't you just have to download crap to fill it up?
or just cat /dev/zero > file .. and that file'll grow until your harddrive's full

but really, i just have no idea what you're talking about

---

### Post by solwic on 2009-10-02
> **renkinjutsu said:**
> I'm just posting because i'm curious..
What do you mean by shredding unused space? .. like the unpartitioned space that shows up in gparted? or like... free space that hasn't been used yet? Then wouldn't you just have to download crap to fill it up?
or just cat /dev/zero > file .. and that file'll grow until your harddrive's full

but really, i just have no idea what you're talking about

When you delete a file, it isn't really removed.  The system just "forgets" about it.  It's still there, written on the disk, until you download something else that overwrites it.

Shredding overwrites all that previously used space with random garbage so that the files that used to be there can't be recovered (at least, it's much more difficult).  

The "shred" command is built in to the shell.  Thus: 

```
shred -vuzfn 50 file.name
```

would overwrite the specified file with 50 passes of random garbage.  Problem is, "shred" doesn't do unused space, only individual files.  

The link above is for a file called "Secure Delete", and it has commands to shred files as well as RAM and free space that has been used before, but isn't now (which is where deleted files live).  

Make sense?  (Somebody correct me if I've gotten any of that wrong)

*NOTE:  So far so good with sfill.  The site says that it's hard with journaling systems to get all the free space, but that there's no way around it.  Most shredded is better than none shredded, I guess....  Thanks again for the link.  :biggrin:

---

### Post by solitaire on 2009-10-02
best way to "wipe" empty space is to use the "dd" command..

```
sudo dd if=/dev/zero of=/home/[your username]/wipe.file
```
once it's finished run ```
rm /home/[your username]/wipe.file
```
The first command basically create a file called "wipe.file" and keep filling it with zero's till the disk is full.
You could use /dev/urandom instead which will fill the file with random data.
if you don't use sudo then all but 5% of the will be used (5% is reseved for the root login)

it might take a while depending on how big your drive is...

---

### Post by solwic on 2009-10-02
> **solitaire said:**
> best way to "wipe" empty space is to use the "dd" command..

```
sudo dd if=/dev/zero of=/home/[your username]/wipe.file
```
once it's finished run ```
rm /home/[your username]/wipe.file
```
The first command basically create a file called "wipe.file" and keep filling it with zero's till the disk is full.
You could use /dev/urandom instead which will fill the file with random data.
if you don't use sudo then all but 5% of the will be used (5% is reseved for the root login)

it might take a while depending on how big your drive is...

Which essentially does what secure delete and shred do:  fill your drive with garbage, then wipe the garbage out.  

Good idea.  Might experiment with it, research it a little.  :)

---

### Post by renkinjutsu on 2009-10-03
heey! i offered the same advice without even knowing what the OP wanted!

anyway.. if the data is still stored on the HD, is there a builtin shell command to UNdelete a file also?

---

### Post by solwic on 2009-10-03
> **renkinjutsu said:**
> heey! i offered the same advice without even knowing what the OP wanted!

anyway.. if the data is still stored on the HD, is there a builtin shell command to UNdelete a file also?

Not that I'm aware of.  The only way to undelete that I've found is complicated and involves two or three programs.  Must have something to do with the journaling filesystems, because there's a freeware Windows program that works wonderfully on NTFS drives.

---

### Post by Andrew.Z on 2009-10-18
> **iRun said:**
> Thanks.  Will try it now.  Anybody know of any others?

Since [version 0.6.1 BleachBit erases unused hard dive space](http://bleachbit.blogspot.com/2009/08/bleachbit-061-released.html).  

> **solitaire said:**
> best way to "wipe" empty space is to use the "dd" command..


Except that doesn't wipe the inodes (file metadata such as file names).  BleachBit wipes the inodes too.

---

### Post by rapt0rjezuz on 2009-11-10
> **solitaire said:**
> best way to "wipe" empty space is to use the "dd" command..

```
sudo dd if=/dev/zero of=/home/[your username]/wipe.file
```once it's finished run ```
rm /home/[your username]/wipe.file
```The first command basically create a file called "wipe.file" and keep filling it with zero's till the disk is full.
You could use /dev/urandom instead which will fill the file with random data.
if you don't use sudo then all but 5% of the will be used (5% is reseved for the root login)

it might take a while depending on how big your drive is...

You could just make that into a shell script too.

```
#Shredder
sudo dd if=/dev/zero of=/home/[your username]/wipe.file
rm /home/[your username]/wipe.file
```

Simple enough.

---

### Post by wilee-nilee on 2009-11-10
If somebody was able to access your computer for this deleted information chances are they also have the ability to recover some of it no matter what you do.

---

### Post by rapt0rjezuz on 2009-11-10
> **wilee-nilee said:**
> If somebody was able to access your computer for this deleted information chances are they also have the ability to recover some of it no matter what you do.
The previous answer is pretty good, however it is argued that you can recover a zeroed hard drive. It is possible to retrieve \"some\" data however \"fully recovering\" a zeroed hard drive hasn't been done as far as i know.


simply doing a \"1 zero pass\" will invert all the \"1's\" to \"0's\" (remember there are only 1's and 0's) hence \"zeroing\" however there is software available that can detect newly magnetized \"0's\" it simply re-inverts the \"0's\" to \"1's\" if you do a \"7 zero pass\" it's pretty much impossible to retrieve any information off the hard drive. look into the \"DoD 5220.22-m\" standard or \"gutmann\".

---

### Post by alphaniner on 2009-11-10
There was a website offering a prize to anyone that could recover data from a once-dd-zero'd drive.  Granted, the prize was rather paltry, but if it's so easy you gotta wonder...

Also, I didn't see it mentioned that you can create a partition encompassing that unused space and **shred /dev/sd****, or just shred a whole drive.

---


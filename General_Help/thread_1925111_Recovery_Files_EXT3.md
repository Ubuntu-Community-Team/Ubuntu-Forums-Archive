---
title: "Recovery Files EXT3"
date: 2012-02-14
forum: General Help
---

### Post by Autrax on 2012-02-14
Hello!

I accidentally deleted the files, and want to restore it.

HELP PLEASE...

---

### Post by winh8r on 2012-02-14
You can try:

```
sudo apt-get install testdisk
```

there is a step by step guide at [http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step]("http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step")

or you can try:


[http://extundelete.sourceforge.net/]("http://extundelete.sourceforge.net/") to recover entire partition in ext3 or ext4


IMPORTANT Please make sure that you read the documentation about what each product does and understand it BEFORE commencing any recovery. Once you have read it, if you are still unsure, ask a question in the forum before you go and do something that might make the situation worse.

hope this helps you

---

### Post by Autrax on 2012-02-14
Thanks, but **testdisk** not work for me. He finds nothing.  :(

```
No file found, filesystem seems damaged.
```

**Photorec** does not restore the names of folders and files and directory structure (tree). 

**extundelete** will restore it? I dont know it program. :(


**ext3grep** can do it. But in ext3grep i have error (((

```
ext3grep: init_directories.cc:534: void init_directories(): Assertion `lost_plus_found_directory_iter != all_directories.end()' failed.
```

But it creates a file with a list of deleted files and directories, there are also the address.


**R-Linux** restores a lot of inodes, but does not restore my folder with the names and directory structure.

**ext3undel** and **foremost** too not can help me?

**extundelete** can help me, do you think it?

---

### Post by winh8r on 2012-02-14
> **Autrax said:**
> Hello!

I accidentally deleted the files, and want to restore it.

HELP PLEASE...


I would think that extundelete would be able to do it too.

Did you run Photorec?

Or did you not run it because it would not bring everything back exactly as it was before you deleted it?

You will need to download extundelete and compile it before you can run it.

---

### Post by Autrax on 2012-02-14
I edited my past post.

I ran **photorec**, he created a folder in each folder were files with the same extension. 
One folder - one extension.

There has not was recovered names and directories.

And not all files work, the many archives did not run and etc.

I do not fit **photorec**.

---

### Post by Autrax on 2012-02-14
```
sudo apt-get install extundelete
```

Installation is complete.

What to do next?

---

### Post by winh8r on 2012-02-14
For full info/options for recovery

type


```
extundelete --help
```

---

### Post by Autrax on 2012-02-14
Oh thank process is run,
but I see a lot of messages in the form:

```
Failed to restore inode 499828 to file RECOVERED_FILES/deleted_folder/Root/deleted_folder/.opera/opcache:Inode does not correspond to a regular file.
```

Very many these messages :(

HELP PLEASE!

---

### Post by winh8r on 2012-02-14
Make sure you have the path to the file correctly written.

If path to single file is correct and it will not recover then try running



```
extundelete /dev/sdb --restore-all
```

---

### Post by Autrax on 2012-02-14
If will not work with sdb5, then use just sdb, yes?

---

### Post by Autrax on 2012-02-14
How to write to the Canonical to include and activate GIIS ([http://www.giis.co.in/](http://www.giis.co.in/)) program in default standart Ubuntu version?

And a request to make a general GUI to recover data from different file systems (ext2,3,4/NTFS/FAT16,32/Btrfs...), GUI for many console programs, one for all?

---

### Post by Autrax on 2012-02-14
Advantage (used) of the program **Photorec** and got only one seventh (1/7) of my files. In addition, all the names and directory structure is destroyed.

**extundelete** rebuilt almost the entire volume of files, restored all the names and directory structure, some files are not restored, and some files with errors, this is likely due to the program autochetsk.

Thank You, **winh8r**!

---

### Post by Autrax on 2012-02-15
UFS Explorer - this is a program for recovery. But it is shareware/trial :(
In addition, I have freezes and crash (program is not responding/ Denial of Service) at work.

---

### Post by dragonfly41 on 2012-02-15
> And a request to make a general GUI to recover data from different file  systems (ext2,3,4/NTFS/FAT16,32/Btrfs...), GUI for many console  programs, one for all? 

Here is yet another recovery tool .. but as with all commercial software you usually "try and buy" 

[http://www.stellarinfo.com/linux-data-recovery.htm](http://www.stellarinfo.com/linux-data-recovery.htm)

.. there are several others .. e.g. .. [http://www.getbackdata.net/](http://www.getbackdata.net/)

Have you tried **scalpel** (in Synaptics Package Manager)?

Note that with recovery software it is safer to run in Live CD.

---

### Post by Autrax on 2012-02-15
**scalpel** - is just a toy. He had very little help.

---

### Post by dragonfly41 on 2012-02-15
> **scalpel** - is just a toy. He had very little help. 

Here is the description ..

> [B]Scalpel: A Frugal, High Performance File Carver
[/B]

   Scalpel is a fast file carver that reads a database of header and footer definitions and extracts matching files or data fragments from a set of image files or raw device files. Scalpel is filesystem-independent and will carve files from FATx, NTFS, ext2/3, HFS+, or raw partitions. It is useful for both digital forensics investigation and file recovery. 


---

### Post by Autrax on 2012-02-15
Thanks I have worked with him.

---

### Post by winh8r on 2012-02-15
It is important to remember that there are quite a few different recovery tools available, each has their own strengths and weaknesses. It is always advisable to spend as much time as possible researching how each tool works and whether or not it is right for the specific problem you are having.

The need for data recovery tools is largely brought about by people not observing one basic rule of computer usage, which is BACK UP YOUR DATA.

Even if you only back up your home folder every week, it will put you in a position where you will still have access to your valuable documents, photographs,music etc. if something catastrophic happens to your main disk/partition.

Further to this , if you do accidentally delete a partition or a directory then it is important to stop using that device as soon as possible after you discover your mistake. Continuing to use the device will reduce the chances of successfully recovering deleted data as the operating system will see the space where the partition was as "available space" and will write further data to it, possibly corrupting data which was there before.

When running recovery software, always run it from another partition than the the one you are trying to recover from.Or as has been suggested from a Live CD, and ensure that the recovered data is being sent to either an external device or a second hard drive in the machine.

If you do not feel confident about doing data recovery then get as much information as you can and read and re-read it until you fully understand the implications of what you are about to do.

Finally, remember that the data recovery process does not work as quickly as the delete process, you can delete something like a partition with a single command or click of a mouse and the result is instant, however the process required to reverse this can take days to complete, depending on how much data you are trying to recover and the size of the disk or partition involved.

Back up your data at least weekly. It is much less hassle to prepare for it than to recover from it!!


Thanks to other members for their helpful links above, and autrax, I am glad that you managed to get at least some of your data back again after all !!!

---


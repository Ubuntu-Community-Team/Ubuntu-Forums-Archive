---
title: "Testdisk"
date: 2011-11-22
forum: General Help
---

### Post by tommy2k10 on 2011-11-22
First of all, I did check if there were any other posts about Testdisk, which there are, but they all seem to say post your own with however you, as an individual, want to use testdisk.

I have got a 500GB external hard drive, which I accidentally formatted (I cannot remember why!).  I work with computers, and had all my client records on it, which I copied back on from my own machine.  Can I use testdisk to try and recover the files on the drive even though it has been formatted once?  If so, I guess I will have to tell Testdisk that there are no partitions? and just to list the files and recover them.

Or is PhotoRec easier to use in my situation?

---

### Post by raja.genupula on 2011-11-22
yeah they gonna help you ,

plus i wanna give one more thing to you

[http://goinggnu.wordpress.com/2008/02/14/recover-deleted-files-from-memory-card/](http://goinggnu.wordpress.com/2008/02/14/recover-deleted-files-from-memory-card/)

---

### Post by tommy2k10 on 2011-11-22
Thankyou.

This is what I don't understand:

When it says

First thing I did is “**Take a image of memory card**“.
 So,
    

[INDENT]dd if=/dev/sda of=my_card.img bs=512[/INDENT] The file **my_card.img** is the extract copy of my memory card.
It has everything, but as deleted files.


what would my external drive be called.


dd if=/dev/sda of=my_ex_drive.img.bs=512 



??

---

### Post by tommy2k10 on 2011-11-22
Instead of writing commands, doesn't PhotoRec do it automatically?

---

### Post by alphaamanitin on 2011-11-22
Photorec is designed to recover files, NOT restore drives.  

How I restored my HD after doing a quick format from NTFS to FAT32.

Here is what I did:
 shut down the computer and removed the affected drive. 
 I used a  separate computer to create a USB live version of Kubuntu.  
Attached my original drive and a new drive of equal size to a different computer
Booted into Kubuntu
Opened the terminal and cloned my old drive to the new drive with the dd command (in this case [COLOR=#FF0000]sudo dd if=/dev/sdb of=/dev/sda bs=32M[/COLOR] the old drive is /dev/sdb new drive is /dev/sda 'if' means input file, 'of' means output file NEVER MIX THESE UP!)
removed the old drive and rebooted into Windows 7
Download and ran TeskDisk
selected create log
selected my drive and the type of drive
selected analyze
did a quick search-no luck finding the NTFS partition, just the FAT32, sto hit q (though enter would have worked as well I think)
chose deeper search
Success found the NTFS, used arrow keys to go down to it, then hit right arrow to select it.
hit enter
selected write
here you can either rebuild or back up the boot sector (BS) of the partition.  I rebuilt it.
Reboot.  
Success my data was back.
Used SuperGrub to restore the Windows XP boot manager, everything was fine and I got a free back up of my old drive.



[COLOR=red]**WARNING-IMPORTANT INFO AND QUALIFICATIONS!!!**[/COLOR]
If you did the reformatting in windows and did not chose a quick format the data is likely gone.   If you went from a format that has a back up header to another with a back up header it may make things much more difficult.  If the drive is not in good health and experiencing I/O errors any attempt to recover may damage the drive even more.  You probably know all of this, but I thought I would mention it.
AlphaA

---

### Post by raja.genupula on 2011-11-22
> **tommy2k10 said:**
> Thankyou.

This is what I don't understand:

When it says

First thing I did is “**Take a image of memory card**“.
 So,
    
[INDENT]dd if=/dev/sda of=my_card.img bs=512[/INDENT]The file **my_card.img** is the extract copy of my memory card.
It has everything, but as deleted files.


what would my external drive be called.


dd if=/dev/sda of=my_ex_drive.img.bs=512 



??
To know that use this command 
```
sudo blkid
```

its  going to povide the drives with label too . so you can easily identify .
I have given another link and that have few other methods . try them too.

---

### Post by tommy2k10 on 2011-11-23
I ran PhotoRec which found files and put them in 320 directories in the folder I specified.  The text files all open weirdly (they are not as they were!) but I guess they are the deleted 1KB files you mentioned?  How do I get them back to the way they were?

---

### Post by tommy2k10 on 2011-11-23
> **alphaamanitin said:**
> Photorec is designed to recover files, NOT restore drives.  

How I restored my HD after doing a quick format from NTFS to FAT32.

Here is what I did:
 shut down the computer and removed the affected drive. 
 I used a  separate computer to create a USB live version of Kubuntu.  
Attached my original drive and a new drive of equal size to a different computer
Booted into Kubuntu
Opened the terminal and cloned my old drive to the new drive with the dd command (in this case [COLOR=#FF0000]sudo dd if=/dev/sdb of=/dev/sda bs=32M[/COLOR] the old drive is /dev/sdb new drive is /dev/sda 'if' means input file, 'of' means output file NEVER MIX THESE UP!)
removed the old drive and rebooted into Windows 7
Download and ran TeskDisk
selected create log
selected my drive and the type of drive
selected analyze
did a quick search-no luck finding the NTFS partition, just the FAT32, sto hit q (though enter would have worked as well I think)
chose deeper search
Success found the NTFS, used arrow keys to go down to it, then hit right arrow to select it.
hit enter
selected write
here you can either rebuild or back up the boot sector (BS) of the partition.  I rebuilt it.
Reboot.  
Success my data was back.
Used SuperGrub to restore the Windows XP boot manager, everything was fine and I got a free back up of my old drive.



[COLOR=red]**WARNING-IMPORTANT INFO AND QUALIFICATIONS!!!**[/COLOR]
If you did the reformatting in windows and did not chose a quick format the data is likely gone.   If you went from a format that has a back up header to another with a back up header it may make things much more difficult.  If the drive is not in good health and experiencing I/O errors any attempt to recover may damage the drive even more.  You probably know all of this, but I thought I would mention it.
AlphaA


Thankyou.  However, I want my files back from my external drive, so isn't recovering the files from the drive using PhotoRec the same thing?
Also, I have only got 2 250GB drives in my machine, and 320GB of files on my external drive!  Can I clone the 320GB of external drive data to my 500GB drive in my Windows machine, or would it be better to get another external drive to clone it on there?

---

### Post by alphaamanitin on 2011-11-23
No recovering with PhotoRec and TestDisk is no the same thing.  TestDisk is mostly designed to recover partitions and the like, but can be used to recover files.  If you just want the files and not the drive back to the original condition I would try PhotoRec.  If you want to recover the drives original partitions and the like I would use TeskDisk.  PhotoRec is more independent in its file recovery than TestDisk, basically fill in a few options and let it go.  

You could clone to two separate drives, but I am not sure exactly how to do it.  I always clone to a drive of equal or greater size.  You should look into that more, I am not expert on cloning, but I am pretty sure you could split the clone across two drives.  Do you have a friend that you can borrow a drive from?

AlphaA

---

### Post by tommy2k10 on 2011-11-23
I'll ask around.
I didn't set up any partitions on the external drive so I think PhotoRec would be the best.
How can I read the recovered files properly?

---

### Post by alphaamanitin on 2011-11-23
Well, you have to set up a partition on a drive to use the drive, even if it is just one gigantic partition encompassing the entire drive.  The recovered file should open normally.  Merely double click and it should go.  

AlphaA

---

### Post by tommy2k10 on 2011-11-23
What annoys me with running Testdisk in a Windows environment is when you list the files and tell Testdisk where to copy them to, it just says Copying files, it doesn't tell you how many files it has found.

When I did this with PhotoRec, and tried to open a text file, for example, most of the files had only one line, and were all 1KB!

---

### Post by alphaamanitin on 2011-11-23
I have not used PhotoRec, so I don't have any suggestions besides read the manual.  I can say that I have contacted the program writer and he did email me back.  In fact, I was so estatic by my success with TestDisk I donated 25 dollars to him.

AlphaA

---

### Post by tommy2k10 on 2011-11-23
Firstly, let me apologise for all the questions - I am just a Testdisk newbie!

I don't think I was following 'How to undelete files with Testdisk' very well!

Anyway, because I work with computers, I was thinking i may buy another external drive for my personal files, as if my 'personal' external drive goes wrong, I have always got a separate one for my client records!

I have used software for Windows before called Recuva, which is free for personal use, maybe you can tell me the way Testdisk differs in recovery of the data?

---

### Post by tommy2k10 on 2011-11-23
As the partition is one big partition, won't Testdisk tell me there are no partitions found?

As I accidentally formatted the external drive when I did, will it rebuild the partition that I accidentally formated?

---

### Post by alphaamanitin on 2011-11-23
No, there will always be partitions found on a drive that is in *any* format. TestDisk will detect the current format, and a deep scan using TestDisk will detect former formatting and partition schemes.  Recall that I recovered my NTFS drive with Windows XP and data on it after doing a quick format and formatting the *entire* drive to FAT32.  Read the TestDisk directions and what I did do see how.

AlphaA

---

### Post by tommy2k10 on 2011-11-24
I want to make sure I do everything right before I follow your  procedure.  (I was going to follow 'Undelete files from NTFS partitions'  but that won't work will it?)
I have got two 250GB drives in my test  machine (which I am using as my main machine at the moment) and I  (foolishly) tried to undelete the files onto the disk, which made the  disk full up, thus Ubuntu not booting!  
My external drive (that I want to find the files from) is 500GB with 320GB free.
I have got a 500GB drive in my Windows machine, with 434GB free.
The disk in my spare machine is nowhere near big enough.
Would it better to get another 500GB drive, or can I copy it to my Windows machine?
Or doesn't copying come into it?

---

### Post by bookmarking on 2011-11-24
Hello

Anyways Thanks to share this information

---

### Post by tommy2k10 on 2011-11-25
> **tommy2k10 said:**
> First of all, I did check if there were any other posts about Testdisk, which there are, but they all seem to say post your own with however you, as an individual, want to use testdisk.

I have got a 500GB external hard drive, which I accidentally formatted (I cannot remember why!).  I work with computers, and had all my client records on it, which I copied back on from my own machine.  Can I use testdisk to try and recover the files on the drive even though it has been formatted once?  If so, I guess I will have to tell Testdisk that there are no partitions? and just to list the files and recover them.

Or is PhotoRec easier to use in my situation?

Can I please get some answers on this before I start?

---

### Post by tommy2k10 on 2011-11-28
> **alphaamanitin said:**
> Photorec is designed to recover files, NOT restore drives.  

How I restored my HD after doing a quick format from NTFS to FAT32.

Here is what I did:
 shut down the computer and removed the affected drive. 
 I used a  separate computer to create a USB live version of Kubuntu.  
Attached my original drive and a new drive of equal size to a different computer
Booted into Kubuntu
Opened the terminal and cloned my old drive to the new drive with the dd command (in this case [COLOR=#FF0000]sudo dd if=/dev/sdb of=/dev/sda bs=32M[/COLOR] the old drive is /dev/sdb new drive is /dev/sda 'if' means input file, 'of' means output file NEVER MIX THESE UP!)
removed the old drive and rebooted into Windows 7
Download and ran TeskDisk
selected create log
selected my drive and the type of drive
selected analyze
did a quick search-no luck finding the NTFS partition, just the FAT32, sto hit q (though enter would have worked as well I think)
chose deeper search
Success found the NTFS, used arrow keys to go down to it, then hit right arrow to select it.
hit enter
selected write
here you can either rebuild or back up the boot sector (BS) of the partition.  I rebuilt it.
Reboot.  
Success my data was back.
Used SuperGrub to restore the Windows XP boot manager, everything was fine and I got a free back up of my old drive.



[COLOR=red]**WARNING-IMPORTANT INFO AND QUALIFICATIONS!!!**[/COLOR]
If you did the reformatting in windows and did not chose a quick format the data is likely gone.   If you went from a format that has a back up header to another with a back up header it may make things much more difficult.  If the drive is not in good health and experiencing I/O errors any attempt to recover may damage the drive even more.  You probably know all of this, but I thought I would mention it.
AlphaA

Would this work if I used my 500GB disk in my Windows machine?

I followed this procedure for my external drive, there was no visible difference!

---

### Post by sudodus on 2011-11-28
> Quote:
                                                                      [SIZE=1]Originally Posted by **tommy2k10**                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=11479965#post11479965")[/SIZE]                 
                 [I][SIZE=1]First of all, I did check if there  were any other posts about Testdisk, which there are, but they all seem  to say post your own with however you, as an individual, want to use  testdisk.

I have got a 500GB external hard drive, which I accidentally formatted  (I cannot remember why!).  I work with computers, and had all my client  records on it, which I copied back on from my own machine.  Can I use  testdisk to try and recover the files on the drive even though it has  been formatted once?  If so, I guess I will have to tell Testdisk that  there are no partitions? and just to list the files and recover them.[/SIZE] [SIZE=1]

Or is PhotoRec easier to use in my situation?[/SIZE] [/I]
                                 
Can I please get some answers on this before I start?I'll try:
It is better if you can get the whole partition(s) back with Testdisk or Gpart, because you get the whole structure with directories and file names. So it is worth trying.

Sometimes this does not work, the partition table is too damaged, or the beginning of the partition is overwritten. But on other parts of the hard drive, there may remain data, that belong to your files. Such data can be identified by the file headers and recovered (undeleted) by PhotoRec. I have used it on small amounts of data, and it really works. You can select what kinds of files to recover if you don't want to get lost in thousands of files. I think the reason why one-line text files will be 1 kB is that Photorec recovers data from a file header to the next one (and the chunks are 1kB). This might happen also with picture files, but you don't notice it unless you look at the data with a hex editor (and understand what you look at).

There will be a lot of organizing work, because the directory structure will not be recovered. The files names will also be lost. But I have heard that there is software, that can retrieve file names from some file types, where it is stored inside the file.

Quick formatting should leave the file data, but a full format will overwrite them (as previously stated in this thread). I have read that even overwritten data can be recovered by analyzing faint traces in the magnetic pattern. But I think only the intelligence services of superpower states can afford to do such things.

---

### Post by tommy2k10 on 2011-11-28
Thankyou.
I tried Testdisk, writing a new master partition on my external drive, but it didn't work.  I am now using PhotoRec to try and recover the files.

---

### Post by tommy2k10 on 2011-11-28
Question:
Will the Testdisk procedure work for me (as my previous post said my first attempt didn't) if I attempted to write a master partition on the cloned hard drive, as opposed to the external drive?

---

### Post by tommy2k10 on 2011-11-28
I got some of my files back using PhotoRec (in fact it is still going!)  Maybe the procedure didnt work using Testdisk as I hadn't cloned the disk before.  
Anyway, why can't I read some of the files recovered by PhotoRec and others I can?

---

### Post by oldfred on 2011-11-28
I used photorec to recover some files. Some were text files that I have saved many times and it found every old copy as I had lots of room on drive so not much was overwritten. Sometimes it found bits of files adjacent to each other and combined them into one file, neither was really valid. I created some scripts of my own to sort files into like types and then did a lot of grepping to find data and manually compare files. Not sure I ever found last saved versions as so many were saved, but I recovered a lot of data.

Use scripts to help sort files:
[http://www.cgsecurity.org/wiki/After_Using_PhotoRec](http://www.cgsecurity.org/wiki/After_Using_PhotoRec)
use flac tags to rename files 
[http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html](http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

---

### Post by tommy2k10 on 2011-11-29
One question before I use BuiltBackwards:
Because I am going to use it on a Windows system, I don't have to enter the code that is on the 'after using photorec' page do I?
Also, which BuiltBackwards executable do I want?:
Standalone Executable
Executable + AutoIT v3 source

---

### Post by oldfred on 2011-11-29
Do not know about builtbackwards for Windows.  Unless you want to make some modifications for your use, I would not think you need the source.

Most of the scripts are for Linux but python can run in other systems. When I tried to install python in my XP system with other add-ins it was not exactly easy.

---

### Post by DudeBud on 2011-11-30
Thank you so much for this thread.
I now have hope that photorec could save my ***.

Original thread:
[http://ubuntuforums.org/showthread.php?t=1881540](http://ubuntuforums.org/showthread.php?t=1881540)

I'm gonna work with the options listed in here and, give'er a try.

---

### Post by JKyleOKC on 2011-11-30
> **tommy2k10 said:**
> I got some of my files back using PhotoRec (in fact it is still going!)  Maybe the procedure didnt work using Testdisk as I hadn't cloned the disk before.  
Anyway, why can't I read some of the files recovered by PhotoRec and others I can?I believe that PhotoRec looks for "signatures" to identify which disk block starts a new file, and sometimes finds such a signature on a block that is actually in the middle of another file. In such a situation, it recovers the "new" file it has found -- but since it's only part of another file, it may not be readable by any program.

Almost a year ago I had the equivalent of a disk crash, on a virtual disk that housed my Email files. The virtual disk format is actually an actual file that is treated like a separate disk; my host system needed restarting and during the restart, the virtual disk file was chopped off short, making it unreadable by VirtualBox. I used PhotoRec to attempt recovery of my Email files, with partial success.

However, the recovered files numbered in the thousands, most of which were those unreadable fragments. The ones that could be read were mostly deleted spam messages. I finally decided that recovery of more messages would be more trouble than it was worth. However it did allow me to recover addresses of a number of new clients, and I've kept the "recovered" data in case I need to search it in future.

I did note that PhotoRec claimed recovery of dozens of image files in TIFF and JPG format, when the original damaged disk had almost no such files on it. This is what leads me to believe that the program is looking for format signatures. Even the text files that did turn out to be readable were often only parts of the original files. Still, it's better than nothing -- and it does take a very long time to go through several gigabytes of data. I left it running overnight to get my results.

---


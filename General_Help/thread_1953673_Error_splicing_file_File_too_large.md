---
title: "Error splicing file: File too large"
date: 2012-04-06
forum: General Help
---

### Post by ZJE123 on 2012-04-06
After many problems, I have decided that I need to replace the hard drive on my laptop.  I am about up to the ROOF with anger right now because throughout this process, there has not been one aspect of it that went right.  Here are the problems I have had so far:
1.  Windows would not boot.
2.  Figured out, after a month, that there is a boot error code 0x45d which means I might have to replace the hard drive.
3.  I tried using SMART utility to diagnose the hard drive, that didn't work. 
4.  I tried the disk utility that came with Ubuntu, and that didn't work.
5.  I've given up at this point so I am just gonna scrap the hard drive whether it  is bad or not since I am not going through loads of problems just to figure it out.
But enough of my ranting, here is what I came to this thread for:
6.  I started to copy recovery files from a partition on my main hard drive to my external hard drive (here is where I am now).  It stopped at exactly 4.3GB saying that there was an Error Splicing the file: File too large.

I have read that this is caused by fat32 being on my external hard drive.  I KNOW that this isn't the case with mine because it is a 1.5TB hard drive and I've copied more that 50GB through Windows before.  My question is, how do I make linux copy a virtually unlimited amount of files so that way I can back up my files and replace the hard drive and be done with this headache?  Any help will be appreciated!

---

### Post by coffeecat on 2012-04-06
> **ZJE123 said:**
> 
I have read that this is caused by fat32 being on my external hard drive.  I KNOW that this isn't the case with mine because it is a 1.5TB hard drive and I've copied more that 50GB through Windows before.

The limitation with FAT32 is the size of an individual file. Yes, you can have 50GB or more on a FAT32 filesystem (can't remember the limit offhand), but each file can only be a maximum of 4GB. I don't understand the 4.3GB, but I guess the system was trying and failing to copy a file greater than 4GB.

---

### Post by idoitprone on 2012-04-06
> **ZJE123 said:**
> After many problems, I have decided that I need to replace the hard drive on my laptop.  I am about up to the ROOF with anger right now because throughout this process, there has not been one aspect of it that went right.  Here are the problems I have had so far:
1.  Windows would not boot.
2.  Figured out, after a month, that there is a boot error code 0x45d which means I might have to replace the hard drive.
3.  I tried using SMART utility to diagnose the hard drive, that didn't work. 
4.  I tried the disk utility that came with Ubuntu, and that didn't work.
5.  I've given up at this point so I am just gonna scrap the hard drive whether it  is bad or not since I am not going through loads of problems just to figure it out.
But enough of my ranting, here is what I came to this thread for:
6.  I started to copy recovery files from a partition on my main hard drive to my external hard drive (here is where I am now).  It stopped at exactly 4.3GB saying that there was an Error Splicing the file: File too large.

I have read that this is caused by fat32 being on my external hard drive.  I KNOW that this isn't the case with mine because it is a 1.5TB hard drive and I've copied more that 50GB through Windows before.  My question is, how do I make linux copy a virtually unlimited amount of files so that way I can back up my files and replace the hard drive and be done with this headache?  Any help will be appreciated!

fat32 have some massive limitations such as file size must be within 4 gb. Your post does not explain the details the files you are copying. I am not sure how anyone is able to help other than advise you to use ntfs. It was designed to because fat32 is bad in many ways

[http://en.wikipedia.org/wiki/File_Allocation_Table#FAT32](http://en.wikipedia.org/wiki/File_Allocation_Table#FAT32)

 > Yes, you can have 50GB or more on a FAT32 filesystem (can't remember the limit offhand)
According to wikipedia, 2tb at 512byte sector

---

### Post by ZJE123 on 2012-04-06
> **coffeecat said:**
> The limitation with FAT32 is the size of an individual file. Yes, you can have 50GB or more on a FAT32 filesystem (can't remember the limit offhand), but each file can only be a maximum of 4GB. I don't understand the 4.3GB, but I guess the system was trying and failing to copy a file greater than 4GB.

> **idoitprone said:**
> fat32 have some massive limitations such as file size must be within 4 gb. Your post does not explain the details the files you are copying. I am not sure how anyone is able to help other than advise you to use ntfs. It was designed to because fat32 is bad in many ways

[http://en.wikipedia.org/wiki/File_Allocation_Table#FAT32](http://en.wikipedia.org/wiki/File_Allocation_Table#FAT32)

 
According to wikipedia, 2tb at 512byte sector

Sorry I should have worded it differently.  I have coped one file at about 50GB in size in one time using windows to my hard drive.  Yes fat32 limits the size of the file to 4GB but I have copied larger files before in Windows when it as working. What I am saying is that I am 99.99% that the fat32 limit is not the cause of my problems.  What I am asking is what could be another cause?  Oh, and I said I was copying recovery files that came with Lenovo on the main hard drive to my external hard drive, being about 9GB total.  The exact file that won't copy is called "cdrivebackup.wim"

---

### Post by ZJE123 on 2012-04-06
> **coffeecat said:**
> The limitation with FAT32 is the size of an individual file. Yes, you can have 50GB or more on a FAT32 filesystem (can't remember the limit offhand), but each file can only be a maximum of 4GB. I don't understand the 4.3GB, but I guess the system was trying and failing to copy a file greater than 4GB.

> **idoitprone said:**
> fat32 have some massive limitations such as file size must be within 4 gb. Your post does not explain the details the files you are copying. I am not sure how anyone is able to help other than advise you to use ntfs. It was designed to because fat32 is bad in many ways

[http://en.wikipedia.org/wiki/File_Allocation_Table#FAT32](http://en.wikipedia.org/wiki/File_Allocation_Table#FAT32)

 
According to wikipedia, 2tb at 512byte sector

Here is a picture of the properties of my external hard drive, maybe that will help a little bit.  According to this is says the file system type is msdos, which would point to a fat32 system, I'm guessing.  But that doesn't explain why I have copied larger files before.  I have copied aprox. 407.9GB of data to this hard drive.  If I were to copy all of those files in 4GB intervals, I would have lost patience, knowing myself, so I know that isn't the case either.

---

### Post by idoitprone on 2012-04-07
> **ZJE123 said:**
> Here is a picture of the properties of my external hard drive, maybe that will help a little bit.  According to this is says the file system type is msdos, which would point to a fat32 system, I'm guessing.  But that doesn't explain why I have copied larger files before.  I have copied aprox. 407.9GB of data to this hard drive.  If I were to copy all of those files in 4GB intervals, I would have lost patience, knowing myself, so I know that isn't the case either.

that is not helpful.

The information we need is single file size. You can copy 50 gb or more worth of data. But A single file must be smaller than 4gb

Imagining copying 9gb worth of data
if you have 3 files 3gb each then it is valid
3gb file1
3gb file2
3gb file3

scenerio 2
5gb file1
2gb file2
2gb file3

this will fail because file1 exceeds the limitations of fat32 single file size

---

### Post by coffeecat on 2012-04-07
> **ZJE123 said:**
>  I have coped one file at about 50GB in size in one time using windows to my hard drive.  Yes fat32 limits the size of the file to 4GB but I have copied larger files before in Windows when it as working.

That appears to be a contradiction. You cannot get around the filesize limit of 4GB when copying to FAT32, unless you have some sort of archiving software that splits large files into manageable chunks. You had a file of 50GB in size? That's huge!

---


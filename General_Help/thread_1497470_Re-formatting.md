---
title: "Re-formatting"
date: 2010-05-30
forum: General Help
---

### Post by zolsiemanym on 2010-05-30
hi :) im trying to get my windows files to put on my new ubuntu remix 10.04. would re-formatting the C: drive at fat 32 let me view and edit the files on ubuntu. the reason i ask 'fat 32' is because i saw it on another forum. and would it erase C: drive? thanks :)

---

### Post by Bobhuber on 2010-05-30
> **zolsiemanym said:**
> hi :) im trying to get my windows files to put on my new ubuntu remix 10.04. would re-formatting the C: drive at fat 32 let me view and edit the files on ubuntu. the reason i ask 'fat 32' is because i saw it on another forum. and would it erase C: drive? thanks :)
Ubuntu will be able to see your Windows partition and files without doing anything if that is what you are asking. As far as editing it just depends on the file type. Reformatting drive C: will erase everything on the C: drive.

---

### Post by amite on 2010-05-30
yes,re-formating any drive surely delete all your files on that drive.
but i don't understand why do u want to format ur c drive,coz ubuntu can also read "ntfs" filesystem.

---

### Post by zolsiemanym on 2010-05-30
> **amite said:**
> yes,re-formating any drive surely delete all your files on that drive.
but i don't understand why do u want to format ur c drive,coz ubuntu can also read "ntfs" filesystem.

it wont work on mine :( i installed ubuntu inside windows and i cant access my windows files. ii only installed it as wubi because it wouldent work any other way.

---

### Post by zolsiemanym on 2010-05-30
also it says i have no more space on my hard drive when i clearly have over 100 gig left ? :S

---

### Post by insane_alien on 2010-05-30
perhaps if you did a proper install rather than a wubi install. dual boots are very easy to do.

---

### Post by hansdown on 2010-05-30
Hi zolsiemanym.

I don't have experience with WUBI installs, but please don't format the C drive.

It will erase everything.

---

### Post by Sef on 2010-05-30
> Quote:
 	 	 		 			 				 					Originally Posted by **amite** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=9384952#post9384952") 				
 				[I]yes,re-formating any drive surely  delete all your files on that drive.
but i don't understand why do u want to format ur c drive,coz ubuntu can  also read "ntfs" filesystem.[/I]
 			 		 	 	 
it wont work on mine :sad: i installed ubuntu inside  windows and i cant access my windows files. ii only installed it as wubi  because it wouldent work any other way. 

Have you installed NTFS-3g from the repositories?  Once you do, you will be able to read and write to NTFS.

---

### Post by Mka on 2010-05-30
Do not reformat the C: drive. Leave it as it is. 

I suggest that you uninstall Ubuntu & Wubi under windows and then install Ubuntu properly on its own partition. This is called dual booting. 

In this way, you are guaranteed to access your files in windows under ubuntu whether filesystem is ntfs or fat32.

Good luck.

---

### Post by Sef on 2010-05-30
> Quote:
 	 	 		 			 				 					Originally Posted by **amite** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=9384952#post9384952") 				
 				[I]yes,re-formating any drive surely  delete all your files on that drive.
but i don't understand why do u want to format ur c drive,coz ubuntu can  also read "ntfs" filesystem.[/I]
 			 		 	 	 
it wont work on mine :sad: i installed ubuntu inside  windows and i cant access my windows files. ii only installed it as wubi  because it wouldent work any other way. 

Have you installed NTFS-3g from the repositories?  Once you do, you will be able to read and write to NTFS.

---

### Post by Mka on 2010-05-30
Do not reformat the C: drive. Leave it as it is. 

I suggest that you uninstall Ubuntu & Wubi under windows and then install Ubuntu properly on its own partition. This is called dual booting. 

In this way, you are guaranteed to access your files in windows under ubuntu whether filesystem is ntfs or fat32.

Good luck.

---

### Post by slooksterpsv on 2010-05-30
In Windows if you want to read your Ubuntu partition, you would need to have Ubuntu install as a ext2 or ext3 (haven't had luck with 3) partition and get a 3rd party driver/utility to be able to read ext2/resierfs file systems.

In Ubuntu, it detects your OS, under Places I can see my Gateway HDD listed as: Gateway. Now I have another FAT32 OS that is a recovery partition and another one called System Reserved, which is for Windows 7 - it creates a 100MB Partition for something, I wanna say bitlocker, but I think I'm wrong on that cause bitlocker needs at least 1500MB to work + you have to have ultimate and a TPM chip.

Anyways, NTFS has been really readable under Ubuntu recently, it works quite well. Another thing you can do, in Ubuntu, even Wubi, is try to mount via the Terminal, if you haven't used Terminal, there are guides on here and other places that can help.

Type in the following commands in Terminal (Applications->Accessories->Terminal)
```

sudo parted
***Type in password here***
(parted) print
(parted) quit

```
No under print you should see something like the following:
```

GNU Parted 2.2
Using /dev/sda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) print                                                            
Model: ATA WDC WD5000BEVT-2 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  12.6GB  12.6GB  primary   ntfs
 2      12.6GB  12.7GB  105MB   primary   ntfs            boot
 3      12.7GB  392GB   380GB   primary   ntfs
 4      392GB   500GB   108GB   extended
 5      392GB   401GB   8191MB  logical   linux-swap(v1)
 6      401GB   500GB   99.5GB  logical   ext4

(parted) quit              

```

If I wanted to manually mount the largest partition (the 380GB one), I would type in the following (see how it has a number 3? it would be /dev/sda3 - you can tell what kind your will be via the Disk line up above (mine says Disk /dev/sda: 500GB)):
```

sudo mkdir /media/WIN7PART
sudo mount /dev/sda3 /media/WIN7PART

```

Now I can navigate to:
Places -> Computer -> FileSystem -> media -> WIN7PART 

And I can see all the files in my Windows 7 Partition.

---

### Post by slooksterpsv on 2010-05-30
```


shawn@shawn-ubuntu-laptop:~$ sudo parted
[sudo] password for shawn: 
GNU Parted 2.2
Using /dev/sda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) print                                                            
Model: ATA WDC WD5000BEVT-2 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  12.6GB  12.6GB  primary   ntfs
 2      12.6GB  12.7GB  105MB   primary   ntfs            boot
 3      12.7GB  392GB   380GB   primary   ntfs
 4      392GB   500GB   108GB   extended
 5      392GB   401GB   8191MB  logical   linux-swap(v1)
 6      401GB   500GB   99.5GB  logical   ext4

(parted) quit                                                             
shawn@shawn-ubuntu-laptop:~$ sudo mkdir /media/WIN7PART
shawn@shawn-ubuntu-laptop:~$ sudo mount /dev/sda3 /media/WIN7PART

```

Here's the full Terminal for what I did, cause the above can be confusing

---

### Post by zolsiemanym on 2010-05-30
> **insane_alien said:**
> perhaps if you did a proper install rather than a wubi install. dual boots are very easy to do.

du u reckon you could talk me through it in dumb dumb language
lol

---

### Post by slooksterpsv on 2010-05-30
Dual boots can be difficult to do though, no offense, but here's how I would recommend doing a dual-boot.

I've got an XP so let me attempt to dual-boot.

So I'm booting off of a Ubuntu/Kubuntu install CD. I've got to the partition page (I went to just Install Ubuntu now) - the XP partition is NTFS btw, instructions should be relatively the same:
It says install side by side (on the Kubuntu one), and gives me a dragging arrow on the bottom part to slide how much space to give Kubuntu. So I have a 10GB XP Partition and I want Kubuntu to have 5 so I drag the slider to 5, and choose next, then install.

So pretty much, boot off the CD/DVD of Ubuntu, choose the language then select Install Ubuntu Now. Go through the Language, Keyboard, and Timezone configuration and slide the size of the drive to the amount you want, then choose next and install.

---


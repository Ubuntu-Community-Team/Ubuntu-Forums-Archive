---
title: "Files written from Ubuntu to NTFS aren't read by Windows"
date: 2010-06-07
forum: General Help
---

### Post by danbaark on 2010-06-07
Hi,

I dual boot between Windows 7 and Ubuntu 10.04 (both 64bit) on my laptop with a third (NTFS) partition where I store all my files (documents, media etc...) so that both OSs can read and write to that partition.

This generally seems to be working well except for whenever I write files to the partition from Ubuntu I can access those files fine from Ubuntu but from Windows they are changed to an itc2 file that I can't open.

Examples include a music album where all 12 songs were playable in Ubuntu but formed one single .itc2 file in Windows. Same with a folder of PDF files.

This is pretty much the only thing that's still leaving me unsure about linux so any help as to what's going on would be really appreciated.

Thanks

---

### Post by dino99 on 2010-06-07
i've not experienced with w7, but i use [http://www.fs-driver.org/](http://www.fs-driver.org/) with xp (only /home in ext3 on linux side, and the windows file system: each OS can read/write the other OS filesystem)

[http://www.howtoforge.com/access-linux-partitions-from-windows](http://www.howtoforge.com/access-linux-partitions-from-windows)

---

### Post by danbaark on 2010-06-07
Thanks for the tip but I don't think that really solves my problem. I'm not trying to read or write to a linux partion from windows at all. They both have access to a separate NTFS partition.

In theory they both seem to be able to read and write to it fine (for example I can delete files from it from linux no problem) - it's just that the files I add to it from l despite being written to a windows partition, all seem to be given this funny file extension in windows which I then can't open.

---

### Post by Mark Phelps on 2010-06-07
Sorry I don't have a solution -- but will comment that I do this very stuff on a daily basis (share files between Ubuntus and Win7) and have never encountered the problem you describe.  So, it's not a general Ubuntu-can't-write-to-NTFS-volumes problem.

You could check to see how you're mounting the NTFS volume.  Best results are obtained when you specify a filesystem type of ntfs-3g, rather than nfs or ntfs.

Also, it's generally NOT a good idea to mount an NTFS volume read/write by default (i.e., using your FSTAB) due to the risk of an "unclean shutdown" in Ubuntu -- which then renders your NTFS partition unmountable.  Better to mount it when needed; then unmount it before shutting down.

---

### Post by Barafu Albino Cheetah on 2010-06-07
Are you trying to write to a folder that is a subfolder of encrypted/compressed one? Or may be rights issue. my fstab entry is
```
#UUID=10AE076AAE0747A4 /windows        ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
```
Works great.

---

### Post by danbaark on 2010-06-07
My fstab entry is:

#Entry for /dev/sda6 :
UUID=6601595647ABADD1    /media/Storage    ntfs-3g    
defaults,locale=en_GB.utf8    0    0

I'm hoping that tells you guys more than it does me but I presume it means I have mounted the partition as ntfs-3g rather than just ntfs as suggested.

Also I have my partition automounted on startup and set read/write acces using NTFS configuration tool.

Any ideas? Thanks

---

### Post by stderr on 2010-06-07
To me it sounds potentially like something rather innocent... for example, are there any characters in the filenames of the files you're copying that Winblows can't accept in filenames? 

What does Winblows give as the size of the .itc2 file formed from the mp3s / PDFs? Anything bordering on the total size of the mp3s / PDFs, or something tiny?

---

### Post by dcstar on 2010-06-08
> **Barafu Albino Cheetah said:**
> Are you trying to write to a folder that is a subfolder of encrypted/compressed one? Or may be rights issue. my fstab entry is
```
#UUID=10AE076AAE0747A4 /windows        ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
```
Works great.

Why would a commented out fstab line work at all?

---

### Post by danbaark on 2010-06-12
I actually can't seem to reproduce this error anymore and files seem to write fine now so I'm going to assume I must have done something wrong before that I didn't pick up on and mark this thread solved.

Thanks

---


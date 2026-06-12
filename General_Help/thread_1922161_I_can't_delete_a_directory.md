---
title: "I can't delete a directory"
date: 2012-02-08
forum: General Help
---

### Post by lain80 on 2012-02-08
Hi,
if you read the subject it seems a simple question, but this is the first time that I see a problem like this.
I can't delete a directory, I tried to do a find with inode and rm, but withous success.
The file is saved in a USB HD with the right privileges 
someone can help me?
thanks,
Lain

```

mauri@mauri-laptop:/media/Ext640ntfs/Manuali/Salesforce/Partner Portal$ uname -a
Linux mauri-laptop 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:28:43 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
mauri@mauri-laptop:/media/Ext640ntfs/Manuali/Salesforce/Partner Portal$ df -h
/dev/sde2             295G  200G   80G  72% /media/Ext640ext4
/dev/sde1             297G  226G   72G  76% /media/Ext640ntfs
auri@mauri-laptop:/media/Ext640ntfs/Manuali/Salesforce/Partner Portal$ mount
/dev/sde2 on /media/Ext640ext4 type ext4 (rw,nosuid,nodev,uhelper=udisks)
/dev/sde1 on /media/Ext640ntfs type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
mauri@mauri-laptop:/media/Ext640ntfs/Manuali/Salesforce/Partner Portal$ df -h .
Filesystem            Size  Used Avail Use% Mounted on
/dev/sde1             297G  226G   72G  76% /media/Ext640ntfs
mauri@mauri-laptop:/media/Ext640ntfs/Manuali/Salesforce/Partner Portal$ ls -li
total 64
173902 drwx------ 1 mauri mauri 28672 2012-02-07 12:13 downloaded-content
173789 drwx------ 1 mauri mauri 36864 2012-02-07 12:10 salesforce-downloaded-content
mauri@mauri-laptop:/media/Ext640ntfs/Manuali/Salesforce/Partner Portal$ 
mauri@mauri-laptop:/media/Ext640ntfs/Manuali/Salesforce/Partner Portal$ 
mauri@mauri-laptop:/media/Ext640ntfs/Manuali/Salesforce/Partner Portal$ find . -inum 173789 -exec rm -irf {} \;
mauri@mauri-laptop:/media/Ext640ntfs/Manuali/Salesforce/Partner Portal$ ls -li
total 64
173902 drwx------ 1 mauri mauri 28672 2012-02-07 12:13 downloaded-content
173789 drwx------ 1 mauri mauri 36864 2012-02-07 12:10 salesforce-downloaded-content
mauri@mauri-laptop:/media/Ext640ntfs/Manuali/Salesforce/Partner Portal$ rm -rf salesforce-downloaded-content/
mauri@mauri-laptop:/media/Ext640ntfs/Manuali/Salesforce/Partner Portal$ ls -li
total 64
173902 drwx------ 1 mauri mauri 28672 2012-02-07 12:13 downloaded-content
173789 drwx------ 1 mauri mauri 36864 2012-02-07 12:10 salesforce-downloaded-content
mauri@mauri-laptop:/media/Ext640ntfs/Manuali/Salesforce/Partner Portal$ touch prova
mauri@mauri-laptop:/media/Ext640ntfs/Manuali/Salesforce/Partner Portal$ ls -li
total 64
173902 drwx------ 1 mauri mauri 28672 2012-02-07 12:13 downloaded-content
173978 -rw------- 1 mauri mauri     0 2012-02-07 12:32 prova
173789 drwx------ 1 mauri mauri 36864 2012-02-07 12:10 salesforce-downloaded-content
mauri@mauri-laptop:/media/Ext640ntfs/Manuali/Salesforce/Partner Portal$ rm prova 
mauri@mauri-laptop:/media/Ext640ntfs/Manuali/Salesforce/Partner Portal$ ls -li
total 64
173902 drwx------ 1 mauri mauri 28672 2012-02-07 12:13 downloaded-content
173789 drwx------ 1 mauri mauri 36864 2012-02-07 12:10 salesforce-downloaded-content
mauri@mauri-laptop:/media/Ext640ntfs/Manuali/Salesforce/Partner Portal$ ls -lhd .
drwx------ 1 mauri mauri 312 2012-02-07 12:32 .
mauri@mauri-laptop:/media/Ext640ntfs/Manuali/Salesforce/Partner Portal$ 
mauri@mauri-laptop:/media/Ext640ntfs/Manuali/Salesforce/Partner Portal$ 
mauri@mauri-laptop:/media/Ext640ntfs/Manuali/Salesforce/Partner Portal$ rmdir salesforce-downloaded-content/
rmdir: failed to remove `salesforce-downloaded-content/': No such file or directory
mauri@mauri-laptop:/media/Ext640ntfs/Manuali/Salesforce/Partner Portal$ 

```
this happened when I connect my usb hd to my laptop
```

[15703.526276] usb 2-1.1: new high speed USB device number 8 using ehci_hcd
[15703.707723] scsi11 : usb-storage 2-1.1:1.0
[15705.582722] scsi 11:0:0:0: Direct-Access     Samsung  S2 Portable 3    2AJ1 PQ: 0 ANSI: 0
[15705.582856] scsi: killing requests for dead queue
[15705.587511] scsi: killing requests for dead queue
[15705.587676] scsi: killing requests for dead queue
[15705.604889] scsi: killing requests for dead queue
[15705.612805] scsi: killing requests for dead queue
[15705.612974] scsi: killing requests for dead queue
[15705.622507] scsi: killing requests for dead queue
[15705.630833] scsi: killing requests for dead queue
[15705.642331] sd 11:0:0:0: Attached scsi generic sg5 type 0
[15705.643783] sd 11:0:0:0: [sde] 1250263728 512-byte logical blocks: (640 GB/596 GiB)
[15705.645405] sd 11:0:0:0: [sde] Write Protect is off
[15705.645413] sd 11:0:0:0: [sde] Mode Sense: 23 00 00 00
[15705.646313] sd 11:0:0:0: [sde] No Caching mode page present
[15705.646321] sd 11:0:0:0: [sde] Assuming drive cache: write through
[15705.649526] sd 11:0:0:0: [sde] No Caching mode page present
[15705.649532] sd 11:0:0:0: [sde] Assuming drive cache: write through
[15705.652894]  sde: sde1 sde2
[15705.657639] sd 11:0:0:0: [sde] No Caching mode page present
[15705.657646] sd 11:0:0:0: [sde] Assuming drive cache: write through
[15705.657651] sd 11:0:0:0: [sde] Attached SCSI disk
[15706.115619] EXT4-fs (sde2): mounted filesystem with ordered data mode. Opts: (null)

```

---

### Post by HiImTye on 2012-02-08
try it without the /
```
mauri@mauri-laptop:/media/Ext640ntfs/Manuali/Salesforce/Partner Portal$ rmdir salesforce-downloaded-content[COLOR=Lime]/[/COLOR]
rmdir: failed to remove `salesforce-downloaded-content[COLOR=Lime]/[/COLOR]': No such file or directory
```

---

### Post by oldos2er on 2012-02-08
Are there files in **salesforce-downloaded-content** ? rmdir only removes empty directories.

---

### Post by jamesisin on 2012-02-08
Use tab completion instead of typing out the directory name yourself.  This will be useful if there is a character you cannot see or is being misrepresented.

(If they directory is not yet empty you can use rm /path/to/directory/* to empty it of files.  Again, use tab completion instead of typing out the path.)

---

### Post by lain80 on 2012-02-08
Thanks to all for the answer, but I've did every thing.
read my initial post
[HTML]
mauri@mauri-laptop:/media/Ext640ntfs/Manuali/Salesforce/Partner Portal$ find . -inum 173789 -exec rm -irf {} \;
[/HTML]
with inum and rm -rf you can:
- remove every file or folder (it's the same because it's recursive remove)
- with inum you don't need to select the correct name.

I think that the real problem is this
```

mauri@mauri-laptop:/media/Ext640ntfs/Manuali/Salesforce/Partner Portal$ ls salesforce-downloaded-content/
ls: reading directory salesforce-downloaded-content/: Input/output error

```
but I don't know how can fix it.
thanks to all for any suggest.
Cheers,
Lain

---

### Post by jamesisin on 2012-02-08
You could be looking at some file corruption or drive issue if it's throwing I/O errors.

Did you try using sudo in case there was a permissions problem?

---

### Post by lain80 on 2012-02-09
sorry, I'm just back now.
no it didn't work
```

mauri@mauri-laptop:/media/Ext640ntfs/Manuali/Salesforce/Partner Portal$ sudo find . -inum 173789 -exec sudo rm -rf {} \; -print
./salesforce-downloaded-content
mauri@mauri-laptop:/media/Ext640ntfs/Manuali/Salesforce/Partner Portal$ ls -li
total 36
173789 drwx------ 1 mauri mauri 36864 2012-02-07 12:10 salesforce-downloaded-content
mauri@mauri-laptop:/media/Ext640ntfs/Manuali/Salesforce/Partner Portal$ sudo rm -rf salesforce-downloaded-content*
mauri@mauri-laptop:/media/Ext640ntfs/Manuali/Salesforce/Partner Portal$ ls -li
total 36
173789 drwx------ 1 mauri mauri 36864 2012-02-07 12:10 salesforce-downloaded-content

```

---

### Post by jamesisin on 2012-02-10
Throws no error...

Did you try attaching this drive to another machine to see if the folder is really still there?

---

### Post by lain80 on 2012-02-12
I connected the HD to Windows and tried to delete it but without  success.
I can't delete this directory from windows and linux too.
Someone can help me?
thanks,
Lain


[[IMG]http://img193.imageshack.us/img193/5241/windowsjk.jpg[/IMG]](http://imageshack.us/photo/my-images/193/windowsjk.jpg/)

Uploaded with [ImageShack.us](http://imageshack.us)

---

### Post by jamesisin on 2012-02-12
Let's grasp at straws since we are not getting anywhere...

Try giving full permissions on that directory:

```
chmod 777 /media/Ext640ntfs/Manuali/Salesforce/Partner\ Portal/salesforce-downloaded-content
```

Do the permissions change?

```
ls -al
```

Can you now delete the directory?

```
rmdir -v /media/Ext640ntfs/Manuali/Salesforce/Partner\ Portal/salesforce-downloaded-content
```

Let's take a look at that and see what comes of it.

---

### Post by lain80 on 2012-02-12
nothing happened, it's incredible...this is the first time that I  look at a similar problem.

```

mauri@mauri-laptop:/media/Ext640ntfs/Manuali/Salesforce/Partner Portal$ chmod 777 salesforce-downloaded-content/
mauri@mauri-laptop:/media/Ext640ntfs/Manuali/Salesforce/Partner Portal$ ls -la
total 36
drwx------ 1 mauri mauri     0 2012-02-07 13:21 .
drwx------ 1 mauri mauri     0 2012-02-08 13:35 ..
drwx------ 1 mauri mauri 36864 2012-02-07 12:10 salesforce-downloaded-content
mauri@mauri-laptop:/media/Ext640ntfs/Manuali/Salesforce/Partner Portal$ rmdir -v salesforce-downloaded-content/
rmdir: removing directory, `salesforce-downloaded-content/'
rmdir: failed to remove `salesforce-downloaded-content/': No such file or directory

```

---

### Post by jamesisin on 2012-02-12
What does this show?

```
ls -al /media/Ext640ntfs/Manuali/Salesforce/
```

I am interested in the permissions on Partner Portal...

---

### Post by lain80 on 2012-02-12
I thought the same thing, but on parent folder I can create one more directory without any problem.  

```

mauri@mauri-laptop:/media/Ext640ntfs/Manuali/Salesforce/Partner Portal$ cd ..
mauri@mauri-laptop:/media/Ext640ntfs/Manuali/Salesforce$ ls -la
total 12892
drwx------ 1 mauri mauri        0 2012-02-08 13:35 .
drwx------ 1 mauri mauri     4096 2012-02-07 11:14 ..
drwx------ 1 mauri mauri        0 2012-02-07 13:21 Partner Portal
mauri@mauri-laptop:/media/Ext640ntfs/Manuali/Salesforce$ pwd
/media/Ext640ntfs/Manuali/Salesforce
mauri@mauri-laptop:/media/Ext640ntfs/Manuali/Salesforce$ ls -la
total 12892
drwx------ 1 mauri mauri        0 2012-02-08 13:35 .
drwx------ 1 mauri mauri     4096 2012-02-07 11:14 ..
drwx------ 1 mauri mauri        0 2012-02-07 13:21 Partner Portal
mauri@mauri-laptop:/media/Ext640ntfs/Manuali/Salesforce$ mkdir test
mauri@mauri-laptop:/media/Ext640ntfs/Manuali/Salesforce$ ls -la
total 12893
drwx------ 1 mauri mauri      576 2012-02-12 19:58 .
drwx------ 1 mauri mauri     4096 2012-02-07 11:14 ..
drwx------ 1 mauri mauri        0 2012-02-07 13:21 Partner Portal
drwx------ 1 mauri mauri        0 2012-02-12 19:58 test
mauri@mauri-laptop:/media/Ext640ntfs/Manuali/Salesforce$ rmdir test
mauri@mauri-laptop:/media/Ext640ntfs/Manuali/Salesforce$ ls -la
total 12892
drwx------ 1 mauri mauri      480 2012-02-12 19:58 .
drwx------ 1 mauri mauri     4096 2012-02-07 11:14 ..
drwx------ 1 mauri mauri        0 2012-02-07 13:21 Partner Portal

```

---

### Post by lain80 on 2012-02-16
someone can help me?
thanks for your time.
kind regards,
Lain

---

### Post by erind on 2012-02-16
From your screenshot (and as previously mentioned) it seems that you have a file system corruption, and the drive is NTFS formatted. From my (limited) experience (mostly with NTFS USB flash drives) the only way I've repaired them is through windows tools:

*Mount drive on windows -> My Computer -> Properties (right click your drive) -> Error-checking (check now).*

And when it did not work, I'd backup the data, and reformat the drive. I also keep handy some hard drive health-check and recovery tools, just in case. 

Hope it helps.

---

### Post by lain80 on 2012-02-22
I'm sorry for the late, I just come back.
anyway thanks for your suggest but as per my screenshot it doesn't works so I'll format my HD :(

[[IMG]http://img10.imageshack.us/img10/3681/screenshotat20120222110.png[/IMG]](http://imageshack.us/photo/my-images/10/screenshotat20120222110.png/)

is it incredible that the only path is to follow the format...
thanks anyway and have a great day.

---

### Post by erind on 2012-02-22
Well, according to your screenshot, you're missing two important options during the check:

[LIST]
[*]**Automatically fix file systems errors.**
[*]**Scan for and attempt recovery of bad sectors.**
[/LIST]
You need to* check both* of them and try again. Most of the time I've been able to fix my USB NTFS drives with this check only.

---

### Post by mardybear on 2012-02-22
Just a thought. If your system has a CD or DVD drive, you could also try booting from a live CD, such as Puppy Linux. Sorry if i shouldn't mention other Linux distributions in this forum :)

From my recollection, booting Puppy linux from CD will pretty much allow you to do anything in terms of copying/deleting files/directories. If the live CD approach doesn't work then i agree it's probably some sort of corruption/bad drive problem.

Good luck,

mardybear

---

### Post by lain80 on 2012-02-23
thanks erind, I'm not a lucky guy :P

[[IMG]http://img861.imageshack.us/img861/4849/screenshotat20120223.jpg[/IMG]](http://imageshack.us/photo/my-images/861/screenshotat20120223.jpg/)

mardybear: yep, I'll do it

anyway is incredible how linux can't delete a file and how is a possible that the rm command display back nothing :confused:

---

### Post by lain80 on 2012-02-26
I did a chkdsk, from windows system, and erased the directory.
for me it will be a mister how the rm command didn't show back nothing... :confused:
anyway thanks to all. :D

this is my windows output:
```

Windows PowerShell
Copyright (C) 2009 Microsoft Corporation. All rights reserved.

PS C:\Users\maui> chkdsk J: /f
The type of the file system is NTFS.
Volume label is Ext640ntfs.

CHKDSK is verifying files (stage 1 of 3)...
  177996 file records processed.
File verification completed.
  426 large file records processed.
  0 bad file records processed.
  0 EA records processed.
  0 reparse records processed.
CHKDSK is verifying indexes (stage 2 of 3)...
61 percent complete. (164507 of 221182 index entries processed)
Deleted invalid filename index.html?dir= (167366) in directory 34299.
File 167366 has been orphaned since all its filenames were invalid
Windows will recover the file in the orphan recovery phase.
Correcting minor file name errors in file 167366.
Deleted invalid filename index.html?dir=.%2FMy Books (167367) in directory 34299.
File 167367 has been orphaned since all its filenames were invalid
Windows will recover the file in the orphan recovery phase.
Correcting minor file name errors in file 167367.
Deleted invalid filename index.html?dir=.%2FPhotos (167368) in directory 34299.
File 167368 has been orphaned since all its filenames were invalid
Windows will recover the file in the orphan recovery phase.
Correcting minor file name errors in file 167368.
Deleted invalid filename index.html?dir=.%2FProgramms (167369) in directory 34299.
File 167369 has been orphaned since all its filenames were invalid
Windows will recover the file in the orphan recovery phase.
Correcting minor file name errors in file 167369.
Deleted invalid filename index.html?dir=.&sort_by=muudetud&sort_as=desc (167370) in directory 34299.
File 167370 has been orphaned since all its filenames were invalid
Windows will recover the file in the orphan recovery phase.
Correcting minor file name errors in file 167370.
Deleted invalid filename index.html?dir=.&sort_by=nimi&sort_as=desc (167371) in directory 34299.
File 167371 has been orphaned since all its filenames were invalid
Windows will recover the file in the orphan recovery phase.
Correcting minor file name errors in file 167371.
Deleted invalid filename index.html?dir=.&sort_by=suurus&sort_as=desc (167372) in directory 34299.
File 167372 has been orphaned since all its filenames were invalid
Windows will recover the file in the orphan recovery phase.
Correcting minor file name errors in file 167372.
Deleted invalid filename index.html?D=A (167373) in directory 34314.
File 167373 has been orphaned since all its filenames were invalid
Windows will recover the file in the orphan recovery phase.
Correcting minor file name errors in file 167373.
Deleted invalid filename index.html?D=D (167374) in directory 34314.
File 167374 has been orphaned since all its filenames were invalid
Windows will recover the file in the orphan recovery phase.
Correcting minor file name errors in file 167374.
Deleted invalid filename index.html?M=A (167375) in directory 34314.
File 167375 has been orphaned since all its filenames were invalid
Windows will recover the file in the orphan recovery phase.
Correcting minor file name errors in file 167375.
Deleted invalid filename index.html?M=D (167376) in directory 34314.
File 167376 has been orphaned since all its filenames were invalid
Windows will recover the file in the orphan recovery phase.
Correcting minor file name errors in file 167376.
Deleted invalid filename index.html?N=A (167377) in directory 34314.
File 167377 has been orphaned since all its filenames were invalid
Windows will recover the file in the orphan recovery phase.
Correcting minor file name errors in file 167377.
Deleted invalid filename index.html?N=D (167378) in directory 34314.
File 167378 has been orphaned since all its filenames were invalid
Windows will recover the file in the orphan recovery phase.
Correcting minor file name errors in file 167378.
Deleted invalid filename index.html?S=A (167379) in directory 34314.
File 167379 has been orphaned since all its filenames were invalid
Windows will recover the file in the orphan recovery phase.
Correcting minor file name errors in file 167379.
Deleted invalid filename index.html?S=D (167380) in directory 34314.
File 167380 has been orphaned since all its filenames were invalid
Windows will recover the file in the orphan recovery phase.
Correcting minor file name errors in file 167380.
Deleted invalid filename technote582-1_stat.zip:Zone.Identifier (167386) in directory 35042.
File 167386 has been orphaned since all its filenames were invalid
Windows will recover the file in the orphan recovery phase.
Correcting minor file name errors in file 167386.
Deleted invalid filename technote582-2_coldist.zip:Zone.Identifier (167387) in directory 35042.
File 167387 has been orphaned since all its filenames were invalid
Windows will recover the file in the orphan recovery phase.
Correcting minor file name errors in file 167387.
Deleted invalid filename Thumbs.db:encryptable (167508) in directory 72241.
File 167508 has been orphaned since all its filenames were invalid
Windows will recover the file in the orphan recovery phase.
Correcting minor file name errors in file 167508.
Deleted invalid filename Thumbs.db:encryptable (167509) in directory 75193.
File 167509 has been orphaned since all its filenames were invalid
Windows will recover the file in the orphan recovery phase.
Correcting minor file name errors in file 167509.
Deleted invalid filename Thumbs.db:encryptable (167510) in directory 75363.
File 167510 has been orphaned since all its filenames were invalid
Windows will recover the file in the orphan recovery phase.
Correcting minor file name errors in file 167510.
Deleted invalid filename Thumbs.db:encryptable (167511) in directory 75531.
File 167511 has been orphaned since all its filenames were invalid
Windows will recover the file in the orphan recovery phase.
Correcting minor file name errors in file 167511.
Deleted invalid filename Thumbs.db:encryptable (167512) in directory 75603.
File 167512 has been orphaned since all its filenames were invalid
Windows will recover the file in the orphan recovery phase.
Correcting minor file name errors in file 167512.
Deleted invalid filename Thumbs.db:encryptable (167513) in directory 75620.
File 167513 has been orphaned since all its filenames were invalid
Windows will recover the file in the orphan recovery phase.
Correcting minor file name errors in file 167513.
Deleted invalid filename Thumbs.db:encryptable (167514) in directory 75648.
File 167514 has been orphaned since all its filenames were invalid
Windows will recover the file in the orphan recovery phase.
Correcting minor file name errors in file 167514.
Deleted invalid filename Thumbs.db:encryptable (167515) in directory 75760.
File 167515 has been orphaned since all its filenames were invalid
Windows will recover the file in the orphan recovery phase.
Correcting minor file name errors in file 167515.
Deleted invalid filename Thumbs.db:encryptable (167516) in directory 75771.
File 167516 has been orphaned since all its filenames were invalid
Windows will recover the file in the orphan recovery phase.
Correcting minor file name errors in file 167516.
Deleted invalid filename Thumbs.db:encryptable (167517) in directory 75783.
File 167517 has been orphaned since all its filenames were invalid
Windows will recover the file in the orphan recovery phase.
Correcting minor file name errors in file 167517.
Deleted invalid filename Thumbs.db:encryptable (167550) in directory 76177.
File 167550 has been orphaned since all its filenames were invalid
Windows will recover the file in the orphan recovery phase.
Correcting minor file name errors in file 167550.
Deleted invalid filename Thumbs.db:encryptable (167628) in directory 167553.
File 167628 has been orphaned since all its filenames were invalid
Windows will recover the file in the orphan recovery phase.
Correcting minor file name errors in file 167628.
Deleted invalid filename Thumbs.db:encryptable (167642) in directory 167555.
File 167642 has been orphaned since all its filenames were invalid
Windows will recover the file in the orphan recovery phase.
Correcting minor file name errors in file 167642.
Deleted invalid filename Thumbs.db:encryptable (167646) in directory 36345.
File 167646 has been orphaned since all its filenames were invalid
Windows will recover the file in the orphan recovery phase.
Correcting minor file name errors in file 167646.
Deleted invalid filename Thumbs.db:encryptable (167647) in directory 36441.
File 167647 has been orphaned since all its filenames were invalid
Windows will recover the file in the orphan recovery phase.
Correcting minor file name errors in file 167647.
Deleted invalid filename Thumbs.db:encryptable (167649) in directory 52722.
File 167649 has been orphaned since all its filenames were invalid
Windows will recover the file in the orphan recovery phase.
Correcting minor file name errors in file 167649.
Deleted invalid filename Thumbs.db:encryptable (167650) in directory 52889.
File 167650 has been orphaned since all its filenames were invalid
Windows will recover the file in the orphan recovery phase.
Correcting minor file name errors in file 167650.
Deleted invalid filename Thumbs.db:encryptable (167651) in directory 36404.
File 167651 has been orphaned since all its filenames were invalid
Windows will recover the file in the orphan recovery phase.
Correcting minor file name errors in file 167651.
Deleted invalid filename Thumbs.db:encryptable (167652) in directory 36458.
File 167652 has been orphaned since all its filenames were invalid
Windows will recover the file in the orphan recovery phase.
Correcting minor file name errors in file 167652.
Deleted invalid filename Thumbs.db:encryptable (167654) in directory 51749.
File 167654 has been orphaned since all its filenames were invalid
Windows will recover the file in the orphan recovery phase.
Correcting minor file name errors in file 167654.
Deleted invalid filename Thumbs.db:encryptable (167656) in directory 52088.
File 167656 has been orphaned since all its filenames were invalid
Windows will recover the file in the orphan recovery phase.
Correcting minor file name errors in file 167656.
Deleted invalid filename Thumbs.db:encryptable (167657) in directory 52197.
File 167657 has been orphaned since all its filenames were invalid
Windows will recover the file in the orphan recovery phase.
Correcting minor file name errors in file 167657.
Deleted invalid filename Thumbs.db:encryptable (167658) in directory 51981.
File 167658 has been orphaned since all its filenames were invalid
Windows will recover the file in the orphan recovery phase.
Correcting minor file name errors in file 167658.
Deleted invalid filename Thumbs.db:encryptable (167661) in directory 52292.
File 167661 has been orphaned since all its filenames were invalid
Windows will recover the file in the orphan recovery phase.
Correcting minor file name errors in file 167661.
Deleted invalid filename Thumbs.db:encryptable (167669) in directory 52434.
File 167669 has been orphaned since all its filenames were invalid
Windows will recover the file in the orphan recovery phase.
Correcting minor file name errors in file 167669.
Deleted invalid filename Thumbs.db:encryptable (167670) in directory 52450.
File 167670 has been orphaned since all its filenames were invalid
Windows will recover the file in the orphan recovery phase.
Correcting minor file name errors in file 167670.
Deleted invalid filename Thumbs.db:encryptable (167671) in directory 52461.
File 167671 has been orphaned since all its filenames were invalid
Windows will recover the file in the orphan recovery phase.
Correcting minor file name errors in file 167671.
Deleted invalid filename Thumbs.db:encryptable (167672) in directory 52468.
File 167672 has been orphaned since all its filenames were invalid
Windows will recover the file in the orphan recovery phase.
Correcting minor file name errors in file 167672.
62 percent complete. (167735 of 221182 index entries processed)
Deleted invalid filename Thumbs.db:encryptable (169083) in directory 169066.
File 169083 has been orphaned since all its filenames were invalid
Windows will recover the file in the orphan recovery phase.
Correcting minor file name errors in file 169083.
63 percent complete. (170963 of 221182 index entries processed)
Deleted invalid filename Thumbs.db:encryptable (172433) in directory 52935.
File 172433 has been orphaned since all its filenames were invalid
Windows will recover the file in the orphan recovery phase.
Correcting minor file name errors in file 172433.
Deleted invalid filename Thumbs.db:encryptable (172445) in directory 53460.
File 172445 has been orphaned since all its filenames were invalid
Windows will recover the file in the orphan recovery phase.
Correcting minor file name errors in file 172445.
Deleted invalid filename Thumbs.db:encryptable (172457) in directory 172438.
File 172457 has been orphaned since all its filenames were invalid
Windows will recover the file in the orphan recovery phase.
Correcting minor file name errors in file 172457.
Deleted invalid filename Thumbs.db:encryptable (172461) in directory 172440.
File 172461 has been orphaned since all its filenames were invalid
Windows will recover the file in the orphan recovery phase.
Correcting minor file name errors in file 172461.
Deleted invalid filename Thumbs.db:encryptable (172464) in directory 172441.
File 172464 has been orphaned since all its filenames were invalid
Windows will recover the file in the orphan recovery phase.
Correcting minor file name errors in file 172464.
Deleted invalid filename Thumbs.db:encryptable (172471) in directory 53531.
File 172471 has been orphaned since all its filenames were invalid
Windows will recover the file in the orphan recovery phase.
Correcting minor file name errors in file 172471.
64 percent complete. (174192 of 221182 index entries processed)
Deleted invalid filename Thumbs.db:encryptable (176885) in directory 174198.
File 176885 has been orphaned since all its filenames were invalid
Windows will recover the file in the orphan recovery phase.
Correcting minor file name errors in file 176885.
66 percent complete. (182955 of 221182 index entries processed)
Deleting index entry index.html?dir= in index $I30 of file 34299.
Deleting index entry index.html?dir=.%2FMy Books in index $I30 of file 34299.
Deleting index entry index.html?dir=.%2FPhotos in index $I30 of file 34299.
Deleting index entry index.html?dir=.%2FProgramms in index $I30 of file 34299.
Deleting index entry index.html?dir=.&sort_by=muudetud&sort_as=desc in index $I30 of file 34299.
Deleting index entry index.html?dir=.&sort_by=nimi&sort_as=desc in index $I30 of file 34299.
Deleting index entry index.html?dir=.&sort_by=suurus&sort_as=desc in index $I30 of file 34299.
Deleting index entry index.html?D=A in index $I30 of file 34314.
Deleting index entry index.html?D=D in index $I30 of file 34314.
Deleting index entry index.html?M=A in index $I30 of file 34314.
Deleting index entry index.html?M=D in index $I30 of file 34314.
Deleting index entry index.html?N=A in index $I30 of file 34314.
Deleting index entry index.html?N=D in index $I30 of file 34314.
Deleting index entry index.html?S=A in index $I30 of file 34314.
Deleting index entry index.html?S=D in index $I30 of file 34314.
66 percent complete. (183129 of 221182 index entries processed)
Deleting index entry technote582-1_stat.zip:Zone.Identifier in index $I30 of file 35042.
Deleting index entry technote582-2_coldist.zip:Zone.Identifier in index $I30 of file 35042.
Deleting index entry Thumbs.db:encryptable in index $I30 of file 36345.
Deleting index entry Thumbs.db:encryptable in index $I30 of file 36404.
Deleting index entry Thumbs.db:encryptable in index $I30 of file 36441.
Deleting index entry Thumbs.db:encryptable in index $I30 of file 36458.
67 percent complete. (185139 of 221182 index entries processed)
Deleting index entry Thumbs.db:encryptable in index $I30 of file 51749.
Deleting index entry Thumbs.db:encryptable in index $I30 of file 51981.
Deleting index entry Thumbs.db:encryptable in index $I30 of file 52088.
67 percent complete. (185895 of 221182 index entries processed)
Deleting index entry Thumbs.db:encryptable in index $I30 of file 52197.
Deleting index entry Thumbs.db:encryptable in index $I30 of file 52292.
Deleting index entry Thumbs.db:encryptable in index $I30 of file 52434.
Deleting index entry Thumbs.db:encryptable in index $I30 of file 52450.
Deleting index entry Thumbs.db:encryptable in index $I30 of file 52461.
Deleting index entry Thumbs.db:encryptable in index $I30 of file 52468.
Deleting index entry Thumbs.db:encryptable in index $I30 of file 52722.
Deleting index entry Thumbs.db:encryptable in index $I30 of file 52889.
Deleting index entry Thumbs.db:encryptable in index $I30 of file 52935.
Deleting index entry Thumbs.db:encryptable in index $I30 of file 53460.
67 percent complete. (186025 of 221182 index entries processed)
Deleting index entry Thumbs.db:encryptable in index $I30 of file 53531.
69 percent complete. (191193 of 221182 index entries processed)
Deleting index entry Thumbs.db:encryptable in index $I30 of file 72241.
69 percent complete. (191638 of 221182 index entries processed)
Deleting index entry Thumbs.db:encryptable in index $I30 of file 75193.
Deleting index entry Thumbs.db:encryptable in index $I30 of file 75363.
Deleting index entry Thumbs.db:encryptable in index $I30 of file 75531.
Deleting index entry Thumbs.db:encryptable in index $I30 of file 75603.
Deleting index entry Thumbs.db:encryptable in index $I30 of file 75620.
Deleting index entry Thumbs.db:encryptable in index $I30 of file 75648.
Deleting index entry Thumbs.db:encryptable in index $I30 of file 75760.
Deleting index entry Thumbs.db:encryptable in index $I30 of file 75771.
Deleting index entry Thumbs.db:encryptable in index $I30 of file 75783.
Deleting index entry Thumbs.db:encryptable in index $I30 of file 76177.
71 percent complete. (197936 of 221182 index entries processed)
Deleting index entry Thumbs.db:encryptable in index $I30 of file 167553.
Deleting index entry Thumbs.db:encryptable in index $I30 of file 167555.
71 percent complete. (198061 of 221182 index entries processed)
Deleting index entry Thumbs.db:encryptable in index $I30 of file 169066.
71 percent complete. (198702 of 221182 index entries processed)
Deleting index entry Thumbs.db:encryptable in index $I30 of file 172438.
Deleting index entry Thumbs.db:encryptable in index $I30 of file 172440.
Deleting index entry Thumbs.db:encryptable in index $I30 of file 172441.
Deleting index entry Thumbs.db:encryptable in index $I30 of file 174198.
  221182 index entries processed.
Index verification completed.
CHKDSK is scanning unindexed files for reconnect to their original directory.
  53 unindexed files scanned.
CHKDSK is recovering remaining unindexed files.
  53 unindexed files recovered.
CHKDSK is verifying security descriptors (stage 3 of 3)...
  177996 file SDs/SIDs processed.
Security descriptor verification completed.
  21594 data files processed.
CHKDSK is verifying Usn Journal...
  112032 USN bytes processed.
Usn Journal verification completed.
Correcting errors in the master file table's (MFT) BITMAP attribute.
Correcting errors in the Volume Bitmap.
Windows has made corrections to the file system.

 311315455 KB total disk space.
 237300448 KB in 155945 files.
     66092 KB in 21596 indexes.
         0 KB in bad sectors.
    256343 KB in use by the system.
     65536 KB occupied by the log file.
  73692572 KB available on disk.

      4096 bytes in each allocation unit.
  77828863 total allocation units on disk.
  18423143 allocation units available on disk.
PS C:\Users\maui>

```

---


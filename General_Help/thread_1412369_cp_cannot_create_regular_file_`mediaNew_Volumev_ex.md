---
title: "cp: cannot create regular file `/media/New Volume/v_exam': Operation not supported"
date: 2010-02-21
forum: General Help
---

### Post by ffrr on 2010-02-21
[FONT=Courier New]Hi,

Moving from Windows to Linux is a liberating experience. But the unfamiliar environment makes the acquisition of new working routines a time consuming affair.
      I have been backing up my data on an external hard drive using xcopy. Turning a DOS batch file into a Linux shell script takes a minute. Figuring out why it doesn't work takes hours. So as last resort I turn to this forum.
       I can read files on the external drive, but cannot write anything to it. Here is some configuration data:


1. The bckup script:

cat fromstick.sh

cd "/media/FLASH DRIVE/fre/"
cp -apruv . "/media/New Volume/fre/"
cd "/media/FLASH DRIVE/mysql/DATA/"
cp -apruv . "/media/New Volume/mysql/DATA/"


2. Running the script fails with "Operation not supported" errors.

fr@hatchbox-one:~$ "/media/New Volume/fromstick.sh"

`./DOK/INVENTAR/doku.inv' -> `/media/New Volume/fre/./DOK/INVENTAR/doku.inv'
cp: cannot create regular file `/media/New Volume/fre/./DOK/INVENTAR/doku.inv': Operation not supported
`./DOK/INVEST/v_exam' -> `/media/New Volume/fre/./DOK/INVEST/v_exam'
cp: cannot create regular file `/media/New Volume/fre/./DOK/INVEST/v_exam': Operation not supported
... etc


3. The drives

fr@hatchbox-one:~$ sudo blkid

/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07DA-010E" TYPE="vfat" 
/dev/sda2: LABEL="OS" UUID="07DA-010E" TYPE="vfat" 
/dev/sda5: UUID="04238fe3-34b9-40d1-a410-7cecde32b59f" TYPE="ext4" 
/dev/sda6: UUID="c0842161-6522-4eb4-8fe7-5d34153bdd03" TYPE="swap" 
/dev/sda7: UUID="1C19-7F86" TYPE="vfat" 
/dev/sda8: UUID="f0a0e557-7740-473d-8575-a5f44b3687e0" TYPE="ext4" 
/dev/sdb1: UUID="CAB48993B4898325" LABEL="New Volume" TYPE="ntfs" 


4. mount

fr@hatchbox-one:~$ mount | grep sdb

/dev/sdb1 on /media/New Volume type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


5. Permissions

fr@hatchbox-one:~$ ls -l /media

total 12
lrwxrwxrwx 1 root root    6 2010-02-15 16:48 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2010-02-15 16:48 cdrom0
drwxr-xr-x 2 root root 4096 2010-02-15 16:48 cdrom1
drwx------ 1 fr   fr   4096 2010-02-21 10:31 New Volume
.

fr@hatchbox-one:~$ ls -l "/media/New Volume"

total 3703
-rwxrwxrwx 1 fr fr      12 2008-12-20 20:18 BACKED.NOW
-rwxrwxrwx 2 fr fr 2452967 2008-10-22 09:18 find-d-8a22
drwx------ 1 fr fr    8192 2009-12-28 09:50 fre
-rwxrwxrwx 1 fr fr     147 2010-02-20 10:53 fromstick.sh           <<< The backup script
-rwxrwxrwx 1 fr fr     149 2009-07-15 10:16 FROMSTKD.BAT
-rwxrwxrwx 1 fr fr     149 2009-07-15 10:16 FROMSTKG.BAT
drwx------ 1 fr fr       0 2008-02-24 18:31 mysql
drwx------ 1 fr fr       0 2008-02-24 17:58 System Volume Information


I confess that I find disk partitioning and file systems rather confusing. If this question is naive it won't be hard to answer on a couple of lines.

Thankful for any suggestion

Frederic

 


[/FONT]

---

### Post by lloyd_b on 2010-02-21
The problem appears to be that it's trying to create a directory named "." under "/media/New Volume/fre/", which is a no-no ("." represents the current directory).

Try changing the script to:```
cd "/media/FLASH DRIVE/fre/"
cp -apruv * "/media/New Volume/fre/"
cd "/media/FLASH DRIVE/mysql/DATA/"
cp -apruv * "/media/New Volume/mysql/DATA/"
```

Lloyd B.

---

### Post by egalvan on 2010-02-21
> **ffrr said:**
> 
Moving from Windows to Linux is a liberating experience. But the unfamiliar environment makes the acquisition of new working routines a time consuming affair.

Yes, Linux is Not Windows, but that is one of it's strenghts.

One thing that I returned to when I moved to *.nix was the naming of files, partitions, and drives (CPM & DOS did not like spaces).
I got rid of spaces in the names; usually changed to underscore...

thus...

cd "/media/FLASH DRIVE/mysql/DATA/"
cp -apruv * "/media/New Volume/mysql/DATA/"

becomes...

cd /media/FLASH_DRIVE/mysql/DATA/
cp -apruv * /media/New_Volume/mysql/DATA/


no need to remember to escape or quote spaced variables.
It's the *nix way :)



Oh, and if possible, please keep the forum default font...
it makes it a bit easier to read when scanning dozens of messages.

---

### Post by ffrr on 2010-02-23
Lloyd, thank you for your suggestion:

> Try changing the script to:

> cd "/media/FLASH DRIVE/fre/"
> cp -apruv * "/media/New Volume/fre/"
> cd "/media/FLASH DRIVE/mysql/DATA/"
> cp -apruv * "/media/New Volume/mysql/DATA/"

> Lloyd B.


The dot inside the path goes away, all right, but cp still fails:

`D/0.D' -> `/media/New Volume/fre/D/0.D'
cp: cannot create regular file > /media/New Volume/fre/D/0.D': Operation not supported
... many more 

-------------------------------------------------------------------------------------------

Egalvan, thank you too for your various hints.

> One thing that I returned to when I moved to *.nix was the naming of files, partitions,
> and drives (CPM & DOS did not like spaces).
> I got rid of spaces in the names; usually changed to underscore...

I didn't even know Linux allows white space in names. It's Ubuntu that names the disk "New Volume" when I turn it on and it mounts.


--------------------------------------------------------------------------------------------


I've been playing around another couple of hours and am getting the impression that file names cannot be used on mounted drives. Explicit names can. Any expert to confirm this conclusion?


Frederic


> Oh, and if possible, please keep the forum default font...
> it makes it a bit easier to read when scanning dozens of messages.

I'd be glad to. As a matter of fact I tried to change the font to Courier in order to align the ls lists. It did change for a brief moment and snapped right back to what it was. So I didn't insist to no avail. What is the default font and how do you set it?

---

### Post by lloyd_b on 2010-02-23
Hmmm - I think I see the issue.  You're using the "-a" and "-p" flags on the 'cp' command, which forces 'cp' to preserve the file ownership and permissions.

But you're copying to a VFAT filesystem, which does not support file ownership or file permissions.

Try using "cp -ruv ..." instead, and see if it works.  I realize that you'll lose ownership/permissions metadata doing this, but with a VFAT backup drive there's simply no way to preserve this information.  If you want to preserve that metadata, you'll have to reformat that drive to a filesystem type that supports the metadata (ext2/3, NTFS, etc).

Lloyd B.

---

### Post by ffrr on 2010-02-24
Lloyd,

Thanks again for taking the time. You are probably right suspecting disk formats. Here are the file systems again:

fr@hatchbox-one:~$ sudo blkid
. . .
/dev/sdb1: UUID="CAB48993B4898325" LABEL="New Volume" TYPE="ntfs"     
/dev/sdc1: LABEL="FLASH DRIVE" UUID="6A8A-5C9E" TYPE="vfat"

Note: New Volume is the external disk (destination), shows ntfs
Note: LASH DRIVE is the USB stick (source), shows vfat

fr@hatchbox-one:~$ mount | grep sd
. . .
dev/sdb1 on /media/New Volume type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdc1 on /media/FLASH DRIVE type vfat (rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)

So, the source is vfat and the destination is ntfs. Both devices are read-write. From the command line I can copy files from and to both of the devices in question, also between them, as long as I don't use wild card characters. Any command taking file names, in fact, fails if I use wild cards (ls, mv, cp, cat, etc.) and the error is:  No such file or directory. 
      If we can't get to the bottom of this, it would be a big help if others would confirm the behavior I report as normal systematically (if unsatisfactory). I could then stop spending time with this approach.

Regards

Frederic

---

### Post by lloyd_b on 2010-02-24
> **ffrr said:**
> Lloyd,

Thanks again for taking the time. You are probably right suspecting disk formats. Here are the file systems again:

fr@hatchbox-one:~$ sudo blkid
. . .
/dev/sdb1: UUID="CAB48993B4898325" LABEL="New Volume" TYPE="ntfs"     
/dev/sdc1: LABEL="FLASH DRIVE" UUID="6A8A-5C9E" TYPE="vfat"

Note: New Volume is the external disk (destination), shows ntfs
Note: LASH DRIVE is the USB stick (source), shows vfat

fr@hatchbox-one:~$ mount | grep sd
. . .
dev/sdb1 on /media/New Volume type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdc1 on /media/FLASH DRIVE type vfat (rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)

So, the source is vfat and the destination is ntfs. Both devices are read-write. From the command line I can copy files from and to both of the devices in question, also between them, as long as I don't use wild card characters. Any command taking file names, in fact, fails if I use wild cards (ls, mv, cp, cat, etc.) and the error is:  No such file or directory. 
      If we can't get to the bottom of this, it would be a big help if others would confirm the behavior I report as normal systematically (if unsatisfactory). I could then stop spending time with this approach.

Regards

Frederic

Hmmm.  I was thinking the VFAT disk was the *destination*, but that isn't the problem.  Your destination is NTFS, which *does* support ownership/permission (at least, I assume the NTFS driver for Linux can set ownership/permission on an NTFS drive).

So you can't even run "ls *" on that flash drive without getting an error?  In that case, I would expect that there's a "weird" filename on there that's causing the problem.

My I suggest installing Midnight Commander ("sudo apt-get install mc"), change to that directory, and type "mc" to start it.  Hopefully it'll let you look at the entries in that directory, and if you're lucky you'll be able to spot the "weird" one.

Lloyd B.

---

### Post by ffrr on 2010-02-25
Lloyd,
      After another hour of playing around I think I'm up against a security feature to do with permissions. If I cd to either of the respective drives, everything works fine. If the working directory is other than the drive, and the path component preceding the file name is one of the mounted drives, I can work with files named explicitly. I cannot refer to a selection of files using wild card characters. The error this raises is: No such file or directory. A more explicit message would certainly be a big help.
      At this point I will stop this approach as unworkable and try to think of something else. I thank you very much for your efforts.

Frederic

---

### Post by egalvan on 2010-02-27
> **ffrr said:**
> 
--------------------------------------------------------------------------------------------
 As a matter of fact I tried to change the font to Courier in order to align the ls lists. 


to align text, just enclose it in "code" tags

```
this will 
keep all text   well allinged
 spaces are preserved, etc blah blah     blah
               blah
```

code tags are the "pound" or "number" hash marks at the top of the message window...the third from the right

---

### Post by dcstar on 2010-02-27
> **ffrr said:**
> Lloyd,
      After another hour of playing around I think I'm up against a security feature to do with permissions. If I cd to either of the respective drives, everything works fine. If the working directory is other than the drive, and the path component preceding the file name is one of the mounted drives, I can work with files named explicitly. I cannot refer to a selection of files using wild card characters. The error this raises is: No such file or directory. A more explicit message would certainly be a big help.
      At this point I will stop this approach as unworkable and try to think of something else. I thank you very much for your efforts.

Frederic

You are trying to work with non-Linux filesystems while using Linux wildcard expansion that is designed for Linux filesystems.

FAT and NTFS filesystems do not support certain filenames that are legal under Linux (just try and copy a Linux file that starts with a "." to NTFS...) so it is no surprise that when Linux expands filenames to be Linux compatible that something happens that makes them NTFS incompatible.

You may be better off trying the **mcopy** tool.

---

### Post by bixejo on 2010-03-18
I believe  the problem has nothing to do with wildcards but with some kind of bug in ntfs support in karmic. I've been unable to do anything within one of my directories in the NTFS W7 filesystem, but I can do everything elsewhere in the same filesystem.

Just an example, look:

> 
bixejo@colmena:/media/windows_7/Users/BIXEJO/Mis documentos$ [COLOR=Red]**pwd**[/COLOR]
[COLOR=DimGray]/media/windows_7/Users/BIXEJO/Mis documentos[/COLOR]
bixejo@colmena:/media/windows_7/Users/BIXEJO/Mis documentos$ [COLOR=Red]**mkdir foo**[/COLOR]
**mkdir: cannot create directory  «foo»: Operation not supported**
bixejo@colmena:/media/windows_7/Users/BIXEJO/Mis documentos$ **[COLOR=Red]cd ..[/COLOR]**
bixejo@colmena:/media/windows_7/Users/BIXEJO$ [COLOR=Red]**pwd**[/COLOR]
[COLOR=DimGray]/media/windows_7/Users/BIXEJO[/COLOR]
bixejo@colmena:/media/windows_7/Users/BIXEJO$ **[COLOR=Red]mkdir foo[/COLOR]**
bixejo@colmena:/media/windows_7/Users/BIXEJO$ **[COLOR=Red]ls -ld foo[/COLOR]**
[COLOR=DimGray]drwxrwx--- 1 root plugdev 0 2010-03-18 13:01 foo[/COLOR]
bixejo@colmena:/media/windows_7/Users/BIXEJO$ **[COLOR=Red]mv foo Mis\ documentos[/COLOR]**
bixejo@colmena:/media/windows_7/Users/BIXEJO$ **[COLOR=Red]cd Mis\ documentos/[/COLOR]**
bixejo@colmena:/media/windows_7/Users/BIXEJO/Mis documentos$ **[COLOR=Red]ls -ld foo[/COLOR]**
[COLOR=DimGray]drwxrwx--- 1 root plugdev 0 2010-03-18 13:01 foo[/COLOR]
bixejo@colmena:/media/windows_7/Users/BIXEJO/Mis documentos$ **[COLOR=Red]df -h[/COLOR]**
[COLOR=DimGray]S.ficheros            Tamaño Usado  Disp Uso% Montado en
/dev/sda6              79G  5,7G   70G   8% /
udev                  4,0G  308K  4,0G   1% /dev
none                  4,0G  188K  4,0G   1% /dev/shm
none                  4,0G   92K  4,0G   1% /var/run
none                  4,0G     0  4,0G   0% /var/lock
none                  4,0G     0  4,0G   0% /lib/init/rw
/dev/sda1             245G   61G  184G  25% /media/windows_7
/dev/sdb1             108G   72G   36G  67% /media/windows_xp
/dev/sdb2              33G  5,1G   26G  17% /media/raiz_viejo
/dev/sda7             583G  5,4G  548G   1% /home
/dev/sdb6             7,4G  4,9G  2,1G  71% /media/hogar_viejo[/COLOR]
bixejo@colmena:/media/windows_7/Users/BIXEJO/Mis documentos$ 
So, I cannot create a directory there, but I can create it elsewhere and then move it to there. 

Weird... :-k It's also possible that Windows 7 makes a different use of ntfs filesystem that ntfs Ubuntu support is unable to deal with... I don't know... :roll:

---


---
title: "Best file system for shared data partition?"
date: 2011-07-12
forum: General Help
---

### Post by GuillaumeMG on 2011-07-12
Hi,

I am dual booting ubuntu 11.04 and XP (for games). I made a 3 partitions, 1 for each of the OS and 1 for my music, videos, etc. 

The data partition is currently formated as NTFS but I have some weird trouble where I cannot access some files from XP.

For example, I created a .avi file in ubuntu on the NTFS partition and I can read/write to it from ubuntu. In XP, the .avi will show if I ask for a list of files of it's containing containing folder but I can't play/delete/do anything to it, XP says the path is incorrect.

I was wondering if using ext4 on this partition and installing a driver on xp to be able to read it would be a better solution?

---

### Post by JedMeister on 2011-07-13
But it only officially supported ext2 last time I checked. It does support ext3 too though as I have used it. I don't think it worked with ext4 although that may have changed. There is a warning to only mount ext3 as read only as sometimes Windows does some funky things that mess it up.

I have used NTFS no worries although it pays to run a chdsk every now and again to keep things running smoothly. And it really doesn't like being powered off while still mounted under Linux. FAT is still the most stable cross platform FS IMO.

To avoid this sort of issue (and share files with other PCs) I ended up setting up a Linux fileserver using Samba. From Ubuntu I access via SFTP/SSH (via Nautilus) and from Win I use SMB/CIFS (via Explorer). You can also access Samba shares from Ubuntu if you'd prefer.

---

### Post by wildmanne39 on 2011-07-13
> The data partition is currently formated as NTFS but I have some weird trouble where I cannot access some files from XP.Hi I believe that is because xp can not read ntfs file system.

---

### Post by deserthowler on 2011-07-13
Back when I dual booted, I used FAT32 for my common system and had no problems that I can remember but that was a long time ago.  Ubuntu 5.04 or 5.10.
I still format USB drives in FAT32 just in case I'll need to transfer something to a Windows system.

Earl

---

### Post by JedMeister on 2011-07-13
> **wildmanne39 said:**
> Hi I believe that is because xp can not read ntfs file system.
XP can read NTFS fine. Its the default FS for a clean install of XP.

---

### Post by mastablasta on 2011-07-13
> **GuillaumeMG said:**
>  
For example, I created a .avi file in ubuntu on the NTFS partition and I can read/write to it from ubuntu. In XP, the .avi will show if I ask for a list of files of it's containing containing folder but I can't play/delete/do anything to it, XP says the path is incorrect.
 
 
it's probably a permission issue. you probably unknowingly mark the files as belonging to someone else so the default user on XP can not open them. it would help to know the exact error message but still my suspicion is somethin like that happened. 
 
It should otherwise work just normal. NTFS is the best option in this case. FAT32 can't read big files and also has much larger fragmentation than NFTS.

---

### Post by GuillaumeMG on 2011-07-13
> **JedMeister said:**
> And it really doesn't like being powered off while still mounted under Linux.

I might have done that, multiple times.

> **mastablasta said:**
> it's probably a permission issue. you probably unknowingly mark the files as belonging to someone else so the default user on XP can not open them. it would help to know the exact error message but still my suspicion is somethin like that happened.

It should otherwise work just normal. NTFS is the best option in this case. FAT32 can't read big files and also has much larger fragmentation than NFTS.

I don't have access to my personal computer at the moment but the error message sounded more like "incorrect path" than "permission denied". I will still verify the permissions though, when I come back home.

---

### Post by oldfred on 2011-07-13
Linux uses more characters than windows allows (ascii characters). So did the file name or folder have a character that is not valid in windows?

---

### Post by JedMeister on 2011-07-13
> **GuillaumeMG said:**
> I might have done that, multiple times.

I don't have access to my personal computer at the moment but the error message sounded more like "incorrect path" than "permission denied". I will still verify the permissions though, when I come back home.

Definitely run a chkdsk (from Windows) asap. IMO it is good practice to do that every time your NTFS partition is not unmounted cleanly. I don't boot to Windows that often these days but I try to run it whenever I do.

---

### Post by GuillaumeMG on 2011-07-15
I ran a chkdsk on the partition last night, from windows, it did not solve my problem.

From windows, I can list the files:

```
D:\Videos\Films>dir /b 
    [...] 
    The Karate Kid (1984).avi 
    The Karate Kid (2010).mp4 
    The Kids Are All Right (2010).avi 
    The Land Before Time (1988).mp4 
    The Lord of the Rings: The Fellowship of the Ring (2001).mkv 
    The Lord of the Rings: The Return of the King (2003).mkv 
    The Lord of the Rings: The Two Towers (2002).mkv 
    The Lost Future (2010).avi 
    The Net (1995).avi 
    [...] 
```All the files are ok except for the backup of my 3 LotR dvd I created in ubuntu, windows sees them but it cannot access them:
 
```
D:\Videos\Films>ren "The Lord of the Rings: The Fellowship of the Ring (2001).mkv" foo 
    Le fichier spécifié est introuvable. 
    [translation: File not found.] 
 
D:\Videos\Films>del "The Lord of the Rings: The Fellowship of the Ring (2001).mkv" 
    Syntaxe du nom de fichier, de répertoire ou de volume incorrecte. 
    [translation: Incorrect syntax for file name, directory or volume.] 
```But, from ubuntu, everything is fine with the files, and the permissions are set up like this:

```
guillaume@stegosaure:/media/Données/Videos/Films$ ls -la 
-rw------- 1 guillaume guillaume  838854656 2010-10-12 22:43 The Karate Kid (1984).avi 
-rw------- 1 guillaume guillaume 2230769641 2010-10-24 03:02 The Karate Kid (2010).mp4 
-rw------- 2 guillaume guillaume  733640704 2011-01-28 21:50 The Kids Are All Right (2010).avi 
-rw------- 1 guillaume guillaume  735287666 2011-06-28 20:12 The Land Before Time (1988).mp4 
-rw------- 1 guillaume guillaume 1801950326 2011-06-25 16:44 The Lord of the Rings: The Fellowship of the Ring (2001).mkv 
-rw------- 1 guillaume guillaume 2266872797 2011-06-25 18:21 The Lord of the Rings: The Return of the King (2003).mkv 
-rw------- 1 guillaume guillaume 2107777757 2011-06-25 17:30 The Lord of the Rings: The Two Towers (2002).mkv 
-rw------- 2 guillaume guillaume  730818560 2011-03-13 22:25 The Lost Future (2010).avi 
-rw------- 2 guillaume guillaume  734035968 2011-03-07 06:44 The Net (1995).avi 
```Any other ideas?

---

### Post by Morbius1 on 2011-07-15
> The Lord of the Rings: The Fellowship of the Ring (2001).mkvWindows can't read that file because of all the special characters. You are going to have to mount that partition in fstab and add a special option to resolve this issue permanently..

[1] Unmount the ntfs partition if it is currently mounted.

[2] Create a permanent mount point for the partition:
```
sudo mkdir /media/Data
```[3] Run the following command to get the correct UUID number:
```
sudo blkid -c /dev/null
```You will get something that looks like this:
> /dev/sdc1: UUID="66E4DC83E4DC56C1" TYPE="ntfs"[4] Edit fstab as root and add the following line based on the blkid output:
```
UUID=66E4DC83E4DC56C1 /media/Data ntfs defaults,uid=1000,windows_names,umask=000 0 0
```[5] Save fstab and issue the following command to test for errors and mount the partition:
```
sudo mount -a
```This will prevent Linux from saving a file with a name that Windows cannot read. It won't do anything with the file that's already there so from Linux rename it to something that doesn't have ” * / : < > ? \ | in it's name. You should probably get rid of the "(" and ")" as well.

The windows_names option:
> This option prevents files, directories and extended attributes to be created with a name not allowed by windows, either because it contains some not allowed character (which are the nine characters ” * / : < > ? \ | and those whose code is less than 0×20) or because the last character is a space or a dot. Existing such files can still be read (and renamed).

---

### Post by GuillaumeMG on 2011-07-15
> **Morbius1 said:**
> Windows can't read that file because of all the special characters.
I feel dumb now.

Thank you everyone, you were very helpful! :D

---


---
title: "NTFS partition used to mount but no longer does?"
date: 2010-10-12
forum: General Help
---

### Post by fuzzylogic25 on 2010-10-12
I don't know how this happened as it always worked but once when i restarted it just said before booting into ubuntu that one of the partitions could not be mounted. However it shows the partition label under PLACES. When i try to click it, it says:

Unable to mount WD-DATA
Error mounting: mount exited with exit code1: helper failed with:
[mntent]: line 14 in /etc/fstab is bad
mount: can't find /dev/sda3 in /etc/fstab or /etc/mtab

Does anyone know what this means and how I can fix it?

---

### Post by luvshines on 2010-10-12
What does /etc/fstab file look like ?

---

### Post by fuzzylogic25 on 2010-10-12
how do i find out? sorry im a newbie..

---

### Post by yetiman64 on 2010-10-12
> **fuzzylogic25 said:**
> how do i find out? sorry im a newbie..

Edit: in a terminal use

```
cat /etc/fstab
``` copy and paste the output back here.

---

### Post by fuzzylogic25 on 2010-10-12
================================================================
johny@cmp:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc  nodev,noexec,nosuid       0  0  
# / was on /dev/sda5 during installation
UUID=28875675-d656-441c-b427-746ce917d5e5  /               ext3  errors=remount-ro         0  1  
# swap was on /dev/sda6 during installation
UUID=86f86b69-82de-4650-9de5-3595a01be4ff  none            swap  sw                        0  0  
/dev/fd0                                   /media/floppy0  auto  rw,user,noauto,exec,utf8  0  0  
/dev/sda3                                  /media/WDR [DATA]  ntfs  defaults                    0  0  
================================================================

This is what i got when i did the cat command. The WDR [DATA] partition is what i want to access.

---

### Post by Morbius1 on 2010-10-12
> /dev/sda3                                  /media/WDR**[COLOR=Blue] [DATA][/COLOR]**  ntfs  defaults                    0  0  I think you meant to write:
> /dev/sda3                                  **[COLOR=Blue]/media/WDR-DATA[/COLOR]**  ntfs  defaults                    0  0  This is another issue:
>  mount: can't find /dev/sda3 in /etc/fstab or /etc/mtabYou might want to run the following command which will list all your partitions just to make sure that there really is a /dev/sda3:
```
sudo blkid -c /dev/null
```***[COLOR=Blue]EDIT: [/COLOR]***Actually, if you did create a mountpoint called "WDR [DATA]" you will have to use a special notation in fstab to accommodate the space: "\040". So your fstab line would become:
```
 /dev/sda3 /media/WDR\040[DATA]  ntfs  defaults 0  0
```

---

### Post by fuzzylogic25 on 2010-10-12
==============================================================
john@cmp:~$ sudo blkid -c /dev/null
[sudo] password for john: 
/dev/sda1: LABEL="System Reserved" UUID="702C47912C475170" TYPE="ntfs" 
/dev/sda2: LABEL="WIN7" UUID="E23C57833C575221" TYPE="ntfs" 
/dev/sda3: LABEL="WDR [DATA]" UUID="56106FC3106FA8A7" TYPE="ntfs" 
/dev/sda5: UUID="28875675-d656-441c-b427-746ce917d5e5" TYPE="ext3" 
/dev/sda6: UUID="86f86b69-82de-4650-9de5-3595a01be4ff" TYPE="swap" 
/dev/sdc1: LABEL="DATA-2TB" UUID="c29dea32-2933-4013-881c-f8efb142a5f4" TYPE="ext4" 
/dev/sdb2: LABEL="BU-2TB" UUID="204EDB8C4EDB58DC" TYPE="ntfs"

==============================================================

The name of the partition is "WDR [DATA]" and it is NTFS. It was created under windows and I just now use it under ubuntu. It initially did work perfectly fine until I started trying to configure automount. But I do see that this is the only one that has the space character. What do I need to do now to fix the issue?

---

### Post by Morbius1 on 2010-10-12
> **Morbius1 said:**
> ***[COLOR=Blue]EDIT: [/COLOR]***Actually, if you did create a mountpoint called "WDR [DATA]" you will have to use a special notation in fstab to accommodate the space: "\040". So your fstab line would become:
```
 /dev/sda3 /media/WDR\040[DATA]  ntfs  defaults 0  0
```
Assuming you didn't like the solution above there's no reason you have to create a mount-point of /media/WDR [DATA] just because that's the LABEL of the partition. Create a different one:
```
sudo mkdir /media/WDR-DATA
```Then the line in fstab turns into:
```
/dev/sda3 /media/WDR-DATA  ntfs  defaults 0  0
```

---

### Post by fuzzylogic25 on 2010-10-12
I am a bit confused. I did the "sudo mkdir WDR-DATA" but all that will do is create that empty directory in /media. Its still not mounted to anything?

How will that line in fstab turn into that automatically?

---

### Post by yetiman64 on 2010-10-12
> **fuzzylogic25 said:**
> I am a bit confused. I did the "sudo mkdir WDR-DATA" but all that will do is create that empty directory in /media. Its still not mounted to anything?

How will that line in fstab turn into that automatically?

If you have made the folder and fixed fstab, then run the command,
```
sudo mount -a
```, if all works for you the contents will now be in the folder.
If not post back any error messages the terminal outputs.

---

### Post by Morbius1 on 2010-10-13
> **fuzzylogic25 said:**
> I am a bit confused. I did the "sudo mkdir WDR-DATA" but all that will do is create that empty directory in /media. Its still not mounted to anything?

How will that line in fstab turn into that automatically?
It doesn't change the line automatically.

In retrospect I suppose I should have written my recommendation this way:

Assuming you didn't like the solution above there's no reason you have  to create a mount-point of /media/WDR [DATA] just because that's the  LABEL of the partition. Create a different one:
```
sudo mkdir /media/WDR-DATA 
```Then [COLOR=Blue]change the line in fstab to[/COLOR]:
```
/dev/sda3 /media/WDR-DATA  ntfs  defaults 0  0 
```Then as yetiman64 recommended:
```
sudo mount -a
```

---

### Post by fuzzylogic25 on 2010-10-13
ok well i got it working all good. but now when i run command ls in the media folder that folder WDR-DATA comes up highlighted in GREEN. i look at write permissions using ls -al and get this:


drwxr-xr-x  6 root    root     4096 2010-10-13 21:58 .
drwxr-xr-x 23 root    root     4096 2010-10-13 01:14 ..
drwx------  1 john    john     8192 2010-10-02 00:07 BU-2TB
drwxr-x--- 11 john    john     4096 2010-10-13 21:58 DATA-2TB
drwxrwxrwx  1 root    root     4096 2010-09-30 13:48 WDR-DATA
drwx------  1 john    john     12288 2010-10-11 11:52 WIN7

How do i change this to have ownership similar to the other partitions?

also, what exactly are all these drwx stuff? i know they are some sort of permissions but thats it

---

### Post by Morbius1 on 2010-10-13
>  drwxrwxrwx  1 root    root     4096 2010-09-30 13:48 WDR-DATA>  also, what exactly are all these drwx stuff? i know they are some sort of permissions but thats it     The "d" signifies that it is a directory
A "r" means Read
A "w" mean Write
A "x" means execute ( wich to a directory means "to open" )

The first "rwx" belongs to the owner ( which is root )
The second "rwx" belongs to group ( which is also root )
The last "rwx" belongs to everyone else ( in this case that would be you )

So although root owns the partition the permissions are such that you have full access.

If you realy want to replace root with you then you need to modify the fstab line to look like this:
```
 /dev/sda3 /media/WDR-DATA  ntfs  defaults,uid=1000 0  0
```
The uid=1000 will make you the owner.

---

### Post by fuzzylogic25 on 2010-10-13
ok so my folder contents again (same as before):

drwxr-xr-x 6 root root 4096 2010-10-13 21:58 .
drwxr-xr-x 23 root root 4096 2010-10-13 01:14 ..
drwx------ 1 john john 8192 2010-10-02 00:07 BU-2TB
drwxr-x--- 11 john john 4096 2010-10-13 21:58 DATA-2TB
drwxrwxrwx 1 root root 4096 2010-09-30 13:48 WDR-DATA
drwx------ 1 john john 12288 2010-10-11 11:52 WIN7


then you said:
==================================================
The "d" signifies that it is a directory
A "r" means Read
A "w" mean Write
A "x" means execute ( wich to a directory means "to open" )

The first "rwx" belongs to the owner ( which is root )
The second "rwx" belongs to group ( which is also root )
The last "rwx" belongs to everyone else ( in this case that would be you )
==================================================

This raises some questions:

1. why am i able to create a file and save to it through vim on drives WIN7, BU-2TB & DATA-2TB if only root has rwx permissions?
2. if you say that the last rwx is everyone else and me (username john), then basically, if I want access, EVERYONE else gets access?

---

### Post by Morbius1 on 2010-10-13
You would think I would have learned my lesson from my earlier posts and been way more exact in my descriptions.
>  drwxrwxrwx 1 root root 4096 2010-09-30 13:48 WDR-DATAThe "drwxrwxrwx" is as I have already explained.
The "root root" specifies the owner ( the first "root" ) and the group ( the second "root" )
>  drwx------ 1 john john 12288 2010-10-11 11:52 WIN7For this partition "john" is the owner and the group and the permissions (rwx) are such that only john has access. ( note: root by default has access to everything because it's .. well .. root )
> 2. if you say that the last rwx is everyone else and me (username john),  then basically, if I want access, EVERYONE else gets access?     Nope, you can make the line in fstab do just about anything you want it to. If you want it to look like the WIN7 line it would be:
```
/dev/sda3 /media/WDR-DATA ntfs defaults,uid=1000,gid=1000,umask=077 0 0
```That will make you the owner ( uid=1000) and the group will be set to you ( gid=1000 ) with permissions to allow you full access (the first "0" in umask=077), no access to group ( the first "7") and no access to anyone else ( the last "7")

---

### Post by fuzzylogic25 on 2010-10-13
thanks for all the help, it makes alot of sense now.

ok so i did that:

/dev/sda3    /media/WDR-DATA  ntfs  defaults,uid=1000,gid=1000,umask=077                   0  0  


thats what i have, yet its still the same:
drwxrwxrwx  1 root    root     4096 2010-10-14 01:03 WDR-DATA


so now i wanted to ask two questions if thats ok:

1. why is it still the same lol
2. in the fstab file, why is it that i only see /media/floppy0 and /media/WDR-DATA in there? What about my three other partitions DATA-2TB, BU-2TB and WIN7?
3. what is fstab?

Just in case you need to know, ill show you what my hard disk structure is like

Hard disk 1 Partitions:
1. WIN7 - NTFS
2. WDR-DATA - NTFS
LOGICAL PARTITIONS BELOW:
3. LINUX - EXT3
4. SWAP

Hard disk 2 Partitions:
1. BU-2TB - NTFS

Hard disk 3 Partitions:
1. DATA-2TB - EXT4

The fact that only WDR-DATA is in fstab is strange, dont you think?

---

### Post by Morbius1 on 2010-10-13
>  1. why is it still the same lolfstab is read once during boot so you can make changes but you need to do one of two things to see the affects of the change:

(1) Reboot
OR
(2) Unmount the partition:
```
sudo umount /media/WDR-DATA
```Then tell the system to read fstab and mount everything that hasn't already been mounted:
```
sudo mount -a
```> 2. in the fstab file, why is it that i only see /media/floppy0 and  /media/WDR-DATA in there? What about my three other partitions DATA-2TB,  BU-2TB and WIN7?Unless you do a "Choose the partitions manually" during the inital install Ubuntu will not automatically automount non-system partitions. It has a mechanism to mount them when you need them by having them listed under places. Click on it and they will mount. If you want them to automount they will have to have entries placed in fstab manually.
>  3. what is fstab?**[COLOR=Blue]_f_[/COLOR]**ile **[COLOR=Blue]_s_[/COLOR]**ystem **[COLOR=Blue]_t_[/COLOR]_[COLOR=Blue]ab[/COLOR]_**le

---

### Post by fuzzylogic25 on 2010-10-13
ok makes sense, thanks for that.

i dont know how only WDR-DATA got in there but I would like all my partitions to be automounted. how would i do that?

I would like to also understand the stuff that we are writing to fstab so i can make sense of it all. thanks heaps!

---

### Post by Morbius1 on 2010-10-14
>  ... but I would like all my partitions to be automounted. how would i do that?

I would like to also understand the stuff that we are writing to fstab so i can make sense of it all.Embedded in my babbling throughout this topic is everything you asked for.

(1) Find out how the system sees your partitions:
```
sudo blkid -c /dev/null
```(2) Create permanent homes for the partitions you want to mount:
```
sudo mkdir /media/whatever_you_want
```(3)Add lines in fstab using a template substituting the info from step (1) and (2):
>  /dev/sdxy /media/whatever_you_want ntfs defaults,uid=1000,gid=1000,umask=077 0 0OR
>   /dev/sdxy /media/whatever_you_want  ntfs  defaults,uid=1000 0  0OR even 
>  /dev/sdxy /media/whatever_you_want  ntfs  defaults 0  0

Mounting ex3/4 partitions have different templates than ntfs/fat32 partitions but the process is the same.

---

### Post by fuzzylogic25 on 2010-10-14
ok np i will do that. thanks again for the effort you have put into helping me. i am one hell of a noob and have a lot to learn lol.

---


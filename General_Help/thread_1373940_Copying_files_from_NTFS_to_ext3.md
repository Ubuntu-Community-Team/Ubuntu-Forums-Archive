---
title: "Copying files from NTFS to ext3?"
date: 2010-01-06
forum: General Help
---

### Post by Pipps on 2010-01-06
Hello

I booted in Ubuntu and trying to copy files from an NTFS partition to a separate ext3 partition.

When I enter the following command at the terminal:
> sudo cp /media/CE00E7B800E7A625/Documents and Settings/Administrator/My Documents/1_Music /media/HD2-Media

I receive the following response:
> cp: omitting directory `/media/CE00E7B800E7A625/Documents'
cp: cannot stat `and': No such file or directory
cp: omitting directory `Settings/Administrator/My'
cp: cannot stat `Documents/1_Music': No such file or directory

What could I be doing wrong?:confused:

---

### Post by Leppie on 2010-01-06
this:
> **Pipps said:**
> ```
sudo cp /media/CE00E7B800E7A625/Documents and Settings/Administrator/My Documents/1_Music /media/HD2-Media
```

should be like this:
```
sudo cp /media/CE00E7B800E7A625/Documents\ and\ Settings/Administrator/My Documents/1_Music /media/HD2-Media
```
(without the backslashes the path is seen as multiple arguments as it contains spaces)
or like this:
```
sudo cp "/media/CE00E7B800E7A625/Documents and Settings/Administrator/My Documents/1_Music" /media/HD2-Media
```

---

### Post by Leppie on 2010-01-06
Alternatively, you can use your file manager (like nautilus, konquerer, pcmanfm, thunar, etc.) to copy files using "drag'n'drop" ;)

---

### Post by SecretCode on 2010-01-06
What you are doing wrong is something fairly simple :) ... you can't leave spaces in filenames on the command line (it's true in windows as well). You have to escape them. Either with a backslash before each space, or quotes around the whole name:

So try either of these:
```
sudo cp /media/CE00E7B800E7A625/Documents\ and\ Settings/Administrator/My\ Documents/1_Music /media/HD2-Media 
sudo cp "/media/CE00E7B800E7A625/Documents and Settings/Administrator/My Documents/1_Music" /media/HD2-Media 
```

eta: well there you go. Somebody else knew. :D

---

### Post by Pipps on 2010-01-06
> **Leppie said:**
> should be like this:
```
sudo cp /media/CE00E7B800E7A625/Documents\ and\ Settings/Administrator/My Documents/1_Music /media/HD2-Media
```
(without the backslashes the path is seen as multiple arguments as it contains spaces)
When I copy and paste this directly into the terminal and try again, I now receive the following error message:

> cp: cannot stat `/media/CE00E7B800E7A625/Documents and Settings/Administrator/My': No such file or directory
cp: cannot stat `Documents/1_Music': No such file or directory


I tried using Nautilus in the first instance, but that didn't work either. It simply produced no result whatsoever.

What could I be doing wrong?

---

### Post by Pipps on 2010-01-06
> **SecretCode said:**
> 
```
sudo cp "/media/CE00E7B800E7A625/Documents and Settings/Administrator/My Documents/1_Music" /media/HD2-Media 
```


When I try this code, I also receiving the following error message:

> cp: omitting directory `/media/CE00E7B800E7A625/Documents and Settings/Administrator/My Documents/1_Music'

What could be wrong? :confused:

---

### Post by Morbius1 on 2010-01-06
I'm fairly certain there's another problem. You can't copy a directory using the cp command by itself. You'll get a 

cp: ommitting directory .... error

You need to add the "-R" option:

sudo cp -R "/media/CE00E7B800E7A625/Documents and Settings/Administrator/My Documents/1_Music" /media/HD2-Media

---

### Post by 3rdalbum on 2010-01-06
> **Leppie said:**
> this:


should be like this:
```
sudo cp /media/CE00E7B800E7A625/Documents\ and\ Settings/Administrator/My Documents/1_Music /media/HD2-Media
```
(without the backslashes the path is seen as multiple arguments as it contains spaces)
or like this:
```
sudo cp "/media/CE00E7B800E7A625/Documents and Settings/Administrator/My Documents/1_Music" /media/HD2-Media
```

+1; except it should be:

```
sudo cp -R "/media/CE00E7B800E7A625/Documents and Settings/Administrator/My Documents/1_Music" /media/HD2-Media
```

The -R means "recursive" - it will copy all the files inside the folder.

---

### Post by Pipps on 2010-01-06
> **3rdalbum said:**
> +1; except it should be:

```
sudo cp -R "/media/CE00E7B800E7A625/Documents and Settings/Administrator/My Documents/1_Music" /media/HD2-Media
```

The -R means "recursive" - it will copy all the files inside the folder.
Now THAT works! :D

Thank you one and al! :D

---

### Post by Leppie on 2010-01-06
lol, forgot about that #-o

---

### Post by Pipps on 2010-01-06
I have one more question, if I may.

What if I would like to copy more than one directory in this fashion?

How could I separate the two 'copy from' directories when entering them in only one terminal command?

That is to say, how could I copy multiple directories with just one command?

EDIT: For instance, say I would like to copy both of the following directories:
1. "/media/CE00E7B800E7A625/Documents and Settings/Administrator/My Documents/1_Music"; and
2. "/media/CE00E7B800E7A625/Documents and Settings/Administrator/My Documents/2_Video".

To:
/media/HD2-Media?

How would this be stated in just a single command?

---

### Post by falconindy on 2010-01-06
Brace expansion is the easiest way to do this:

```
cp -r /media/CE00E7B800E7A625/Documents\ and\ Settings/Administrator/My Documents/{1_Music,2_Video} /media/HD2-Media
```

---

### Post by Leppie on 2010-01-06
actually, the easiest way to get around this kind of thing is using bash's tab completion. for example, if you already have this much at the prompt:
```
cp -R /media/CE00E7B800E7A625/Doc
```
try pressing the tab key, it will complete the name the correct way. if there's only 1 file/folder starting with Doc in your c:\, if there's another file/folder starting with doc there it still will take the correct one even though windows is not a case sensitive os. if there's more files/folders, the first time you hit tab won't give you any output but hitting tab again will give you a list with the different options.

---

### Post by Pipps on 2010-01-06
I have a new and related problem! :o

When I now navigate to the folder which holds the newly copied files - *'/media/HD2-Media/'* - I then try to enter the newly copied directory - *'/1_Music'*, I receive the following error message:

> **The folder contents could not be displayed.**
You do not have the permissions necessary to view the contents of "1_Music".

Why could this be, and what could this mean? :confused:

---

### Post by SecretCode on 2010-01-06
It most likely means you do not have permissions necessary to view the contents of that folder.

:wink:

```
ls -l /media/HD2-Media 
```will tell us who is the owner of that folder, and its permissions.

---

### Post by Pipps on 2010-01-07
Hi SecretCode. Thank you for your advice.

I have booted in LiveCD and run the 'ls -l' command. It has returned the following:

> ubuntu@ubuntu:~$ ls -l /media/HD2_Media
total 64
drwx------ 11 root root  4096 Jan  7 09:55 0_Files0
drwx------ 39 root root  4096 Jan  7 09:56 0_Files1
drwx------  2 root root  4096 Jan  7 09:56 0_Files2
drwx------ 19 root root  4096 Jan  7 09:56 0_Law_Study
drwx------ 38 root root  4096 Jan  7 10:54 1_Music
drwx------ 13 root root  4096 Jan  7 10:59 2_Music_projects
drwx------ 10 root root  4096 Jan  7 11:23 3_Video
drwx------ 93 root root  4096 Jan  7 11:46 4_Images
drwx------ 13 root root  4096 Jan  7 11:52 5_Software
drwx------ 10 root root  4096 Jan  7 12:02 6_Books
drwx------ 12 root root  4096 Jan  7 12:03 Ableton
drwx------ 24 root root  4096 Jan  7 12:05 Theming
drwx------  2 root root 16384 Jan  7 09:49 lost+found


I am currently similarly unable to access any of these directories from LiveCD either.

How can I amend the permissions for these directories so that they can be accessed from either LiveCD, Ubuntu or XP?

---

### Post by SecretCode on 2010-01-07
That listing says that only root can access files in those folders.

This is probably because of mount options - either of the HD2_Media drive or the other one. Can you post the contents of the files */etc/fstab* and */etc/mtab*?

---

### Post by Pipps on 2010-01-07
By way of background, I can access the directories happily on the NTFS source drive from which the files were copied from (sda0), even when I am logged into LiveCD. However, I am unable to access the directories on my ext3 backup drive (sdb1) to which they have recently been copied.

On sdb1 I cannot run either fstab or mtab, as it is only a backup drive and contains no Linux installation.

On sda0, it is an XP installation, and so I cannot run fstab or mtab on that drive either.

I have tried accessing fstab and mtab on the LiveCD filesytem. It returns the following:

**fstab**
> aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda5 swap swap defaults 0 0

**mtab**
> 
aufs / aufs rw 0 0
none /proc proc rw,noexec,nosuid,nodev 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
udev /dev tmpfs rw,mode=0755 0 0
/dev/sdd1 /cdrom vfat rw 0 0
/dev/loop0 /rofs squashfs rw 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
tmpfs /tmp tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
none /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/ubuntu/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=ubuntu 0 0
/dev/sda1 /media/CE00E7B800E7A625 fuseblk rw,nosuid,nodev,allow_other,default_permissions,blksize=4096 0 0
/dev/sdb1 /media/HD2_Media ext3 rw,nosuid,nodev,uhelper=devkit 0 0


What can this all mean? :o

---

### Post by SecretCode on 2010-01-07
> **Pipps said:**
> By way of background, I can access the directories happily on the NTFS source drive from which the files were copied from (sda0), even when I am logged into LiveCD. However, I am unable to access the directories on my ext3 backup drive (sdb1) to which they have recently been copied.

Hmm. Then you need to clarify this:

> **Pipps said:**
> When I now navigate to the folder which holds the newly copied files - *'/media/HD2-Media/'* - I then try to enter the newly copied directory - *'/1_Music'*, I receive the following error message:
...

When do you get this error - when booted as live cd, XP, or hard-disk installation of Ubuntu? Give all the details. Then I'll look at the fstab/mtab details.

By the way, PMs are not really necessary - I subscribe to and check on threads I've posted in

---

### Post by Pipps on 2010-01-07
Hi SecretCode. Thank you for the update. I will keep all conversation only to the thread.

I have copied the directories recursively from the sda0 to sdb1 when logged-in under LiveCD, as detailed above.

I now try to access those newly-copied directories residing on sdb1 whilst still logged-into LiveCD. I cannot access them, and receive the aforementioned error message at this point.

I cannot access the newly copied directories using my XP installation which resides on sda0, as sb1 is an ext3 filesystem.

What could be the reason for me to not be able to access these newly copied directories? :confused:

---

### Post by Pipps on 2010-01-07
Update:

I launch nautilus in root, by running 'gksudo nautilus' from the terminal.

I am then able to happily navigate into the newly copied directories located on sdb1.

However, I cannot access these directories by the terminal or in nautilus otherwise.

Could the permissions for these newly copied directories be set too high?

How could I change the permissions of all directories on this sdb1 backup drive, so that they can be access in absolutely every way possible? :-k

---

### Post by audiomick on 2010-01-07
I think the problem is that you don't own them, root does, and no-one else has permission to do anything with them.

You can open nautilus with 
```
gksu nautilus
``` as superuser to change owner and permission via GUI (right click on the directory, properties, permissions tab. You need to click on the button at the bottom to apply the changes to sub-ordinate directories and files)

Via the command line you need "chown" and "chmod"
look at the man pages
```
man chown
```
```
man chmod
```
for an explanation

---

### Post by SecretCode on 2010-01-07
[SIZE="1"]Some typos by the way ... there's no sda0; I think you mean sda1. Also sb1 should obviously be sdb1![/SIZE]

> **Pipps said:**
> I now try to access those newly-copied directories residing on sdb1 whilst still logged-into LiveCD. I cannot access them, and receive the aforementioned error message at this point.
You copied them using 'sudo' and you should be able to access them using 'sudo' ... but that's not really what you want!

:arrow: Try this (from the live CD still)
```
sudo chown a+rwX -R /media/HD2_Media
```
Caution - that makes everything readable and writeable by any user, and may not be ultimately what you want for security. But let's start there.

> **Pipps said:**
> I cannot access the newly copied directories using my XP installation which resides on sda0, as sb1 is an ext3 filesystem.
:shock: Do you want to be able to? I believe there's a driver for XP that can read ext3, but I have never tried it and I don't know if it's any good. If you want access from XP as well as Linux you should use an NTFS drive (partition).

---

### Post by audiomick on 2010-01-07
> **SecretCode said:**
> 
I believe there's a driver for XP that can read ext3, but I have never tried it and I don't know if it's any good.


One that I used on XP that seemed to work well was explore2fs
[http://en.wikipedia.org/wiki/Explore2fs](http://en.wikipedia.org/wiki/Explore2fs)

---

### Post by Leppie on 2010-01-07
> **Pipps said:**
> How could I change the permissions of all directories on this sdb1 backup drive, so that they can be access in absolutely every way possible? :-k

change the partition to ntfs...

---

### Post by Pipps on 2010-01-07
> **SecretCode said:**
> [SIZE="1"]
:arrow: Try this (from the live CD still)
```
sudo chown a+rwX -R /media/HD2_Media
```
Caution - that makes everything readable and writeable by any user, and may not be ultimately what you want for security. But let's start there.

This command returned the following:
> chown: invalid user: `a+rwX'

Should it be modified in any way? :confused:

---

### Post by Leppie on 2010-01-07
i think that should've been chmod, not chown...
chmod is to change the permissions, chown to change owner...

---

### Post by Pipps on 2010-01-07
Hi Leppie. Thank you for the advice!

'sudo chmod a+rwX -R /media/HD2_Media' worked perfectly! :D

---

### Post by Pipps on 2010-01-07
> **audiomick said:**
> One that I used on XP that seemed to work well was explore2fs

I gave the matter a little research prior to choosing an ntfs to ext3 driver interface. I had found ext2fsd to be highly praised, so I tried it.

After only a few minutes of testing, I cannot recommend it highly enough! It would appear to be fully compatible with ext3. I copied a file from ntfs to the ext3 location, using TeraCopy from XP, and then copied that file back from ext3 over to an external FAT32 mp3 player, again using the XP third-party TeraCopy application. All without a hitch. The ext3 driver is now assigned to E:\ in XP, and is fully accessible with fully read and write support.

Everything is now working perfectly! Thank you everyone! Thank you so much! :D

---

### Post by SecretCode on 2010-01-07
Yes, brain-fault there, I meant chmod [SIZE="1"]obviously[/SIZE]

Glad you've got it all fixed!

---


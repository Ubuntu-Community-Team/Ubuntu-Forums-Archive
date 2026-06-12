---
title: "Directory permissions"
date: 2010-11-11
forum: General Help
---

### Post by ianc1 on 2010-11-11
I have what I hope is a simple query regarding directory permissions.  If I create a directory in my home folder it has the following permissions (which I understand is the default directory permissions):

```
drwxr-xr-x
```However directories I copied from my backup have the following permissions:

```
drwx------
```So question one - why?

These copies from the backup were created in my home folder in Ubuntu 10.04 and so presumably originated with a the default directory permissions.

Why should they be different?

Thanks

Ian

---

### Post by TSJason on 2010-11-12
Ian,

I guess the question would be what filesystem are you using on the backup drive and what method are you using to copy the files?

---

### Post by nothingspecial on 2010-11-12
Yep, if you are using a file system that does not support linux file permissions on your backup drive, the permissions will not be preserved.

If you only use linux, consider formatting your backup drive ext3.

---

### Post by bryangwilliam on 2010-11-12
The default permissions allow the owner to read/write/execute , the group to read/execute , and everyone else to read/execute. The permissions you described on the backup only allow the owner to read/write/execute and nothing else.

A agree with the above posts, this is likely from a file system incompatibility. It would be recommended to reformat to a linux supported file system if that is possible for you. In the meantime, doing a chmod 755 on the directory in question should return it to its original state if that is what you want.

---

### Post by Morbius1 on 2010-11-12
How did you do the backup and to what?

A straight copy to an ntfs partition or external device would result in your original permissions being removed as everyone here has said.

But if you created a backup to the same ntfs partition as a compressed tar archive for example then your original permissions should still be intact.

[COLOR=Blue]EDIT:[/COLOR] On reflection it looks like I said the same thing as TSJason but I used a lot more words  :wink:

---

### Post by ianc1 on 2010-11-14
Thanks everyone, sorry for the delayed reply.  My backup is done to a Western Digital drive which came with an NTFS file system which was immediately reformatted before use to EXT4.  I therefore assume that all Linux permissions should be preserved when I either transfer from hard disk to external drive or vice versa.

In answer to how I perform the backup its usually using the desktop file manager by going to Places>Home and copying the folders.  Occasionally the command line is used.

Thanks

---

### Post by Morbius1 on 2010-11-14
Well now that is odd. When I saw the 700 permissions on the directory ( drwx--- ) I jumped to the conclusion that is was an ntfs partition because that's what it does if you mount it through Places.

What are the permissions of the mountpoint itself?

---

### Post by ianc1 on 2010-11-14
Thanks Morbius1.  A thought has just occured to me with all these mentions of NTFS partitions.  In months gone by while changing from Karmic to Lucid I backed everything up before a fresh install and I cannot remember on what.  It will have been a Western Digital external device so its highly likely to have been formatted NTFS although not sure.

I'm unsure what you mean about the permissions of the mount point.

I assume that the following will change the permissions to default for the directory dir, but how can I do it for all directories at once.
```
chmod 755 dir
```Finally is there a file system, other than NTFS, that I can use an external drive that will be read on both Linux and Windows machines and yet still preserve the Linux permissions?

Thanks

---

### Post by Morbius1 on 2010-11-14
Moving it back and forth to an NTFS partition is likely the origin of the problem in this case.

The command you need to change permissions for all of the subdirectories and files withing the directories is:
```
chmod -R 0755 /path-to-dir
```The "-R" is for recursive and will go through every file and directory and change permissions on every one of them.

*[COLOR=Blue] WARNING: The following is only if you are very neurotic:[/COLOR]*
[I]Actually, if you want to be a purist about this the correct way ( at least one one, anyway ) to do this is this way:

[/I]```
sudo find /path-to-dir -type f -print0 | xargs -0 sudo chmod 644
``````
sudo find /path-to-dir -type d -print0 | xargs -0 sudo chmod 755
```[I]The problem with the first method ( chmod -R 0755 ) is that it will do that to directories which is what you want but also to files which you do not want. An odd number ( 7 or 5 ) applied to files will make it executable. And not all files should be executable. The more complicated and longer to execute method will set directory to 755 and files to 644. Admittedly, the fact that you have an innocent text file designated as executable isn't going to end the world.

[/I]> Finally is there a file system, other than NTFS, that I can use an  external drive that will be read on both Linux and Windows machines and  yet still preserve the Linux permissions?There are Linux filesystem drivers that can be installed on Windows that will allow it to R/W to a Linux system but I don't remember what they are as I've never used them.

---

### Post by ianc1 on 2010-11-17
Thanks Morbius1 just the snippet of code I needed.  Also thanks to everyone else for helping me sort this out.

---


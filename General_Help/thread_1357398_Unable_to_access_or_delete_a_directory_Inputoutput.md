---
title: "Unable to access or delete a directory: Input/output error:"
date: 2009-12-17
forum: General Help
---

### Post by bilol on 2009-12-17
Hi everybody,
I am unable to access the directory DKourse:

```
bilol@bilol-desktop:~$ ls /media/DisK4/DKourse/
ls: reading directory /media/DisK4/DKourse/: Input/output error
```

Even I failed to delete the directory:

```
bilol@bilol-desktop:~$ sudo rm -rf  /media/DisK4/DKourse/
[sudo] password for bilol: 
rm: cannot remove directory `/media/DisK4/DKourse': Input/output error
```

Then after a lot of googling, I tried the following to delete DKourse by inode number,but was in vain.

```
bilol@bilol-desktop:~$ ls -dil  /media/DisK4/DKourse/
2518 drwx------ 1 bilol bilol 0 2009-11-09 23:52 /media/DisK4/DKourse/
bilol@bilol-desktop:~$  cd /media/DisK4
bilol@bilol-desktop:/media/DisK4$ find . -inum 2518 -exec  rm -ir {} \;
rm: descend into directory `./.Trash-1000/files/DKourse'? y
rm: remove directory `./.Trash-1000/files/DKourse'? y
rm: cannot remove directory `./.Trash-1000/files/DKourse': Input/output error
rm: descend into directory `./aa/DKourse'? y
rm: remove directory `./aa/DKourse'? y
rm: cannot remove directory `./aa/DKourse': Input/output error
rm: descend into directory `./DKourse'? y
rm: remove directory `./DKourse'? y
rm: cannot remove directory `./DKourse': Input/output error
rm: descend into directory `./EduDocu/DKourse'? y
rm: remove directory `./EduDocu/DKourse'? y
rm: cannot remove directory `./EduDocu/DKourse': Input/output error
rm: descend into directory `./System Volume Information/DKourse'? y
rm: remove directory `./System Volume Information/DKourse'? y
rm: cannot remove directory `./System Volume Information/DKourse': Input/output error


```

Any help will be appreciated......

---

### Post by lazychris2000 on 2009-12-17
Your harddrive may be failing.  I would recommend backing up everything that is important just in case.  If you are running Karmic, there is a utility called palimpsest which will check the SMART status of the drive and let you know if there are any bad sectors on the disk.  System-->Administration-->Disk Utility is where it is located.  You can also run the drive test utility made by the harddrive manufacturer (should be a free download from their website).  If you are unsure of how to use the specific utility, please ask before you do anything with it.  It is VERY easy to format (erase) your drive if you are not careful! Trust me, I have been there.
If the drive is not failing, try running chkdsk on the drive.  Either boot to windows (it looks like you are accessing a windows drive) or boot off of a windows cd and run 'chkdsk /R <drive letter>:'.  On mine, the drive letter is C, but it may be different for you.
Hope that helps!

---


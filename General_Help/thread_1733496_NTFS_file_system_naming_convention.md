---
title: "NTFS file system naming convention"
date: 2011-04-19
forum: General Help
---

### Post by lucast on 2011-04-19
Hi,

I am using NTFS on a partition that I share files between Ubuntu and Windows.  I have a problem for example when I rip music cd's, that quite often it puts characters in the filenames that Windows doesn't like e.g. a question mark or a fullstop at the end of a folder name.

Is it possible to somehow configure either Ubuntu/gnome to not allow certain characters to be written to disk and throw up a warning.  Basically I want to follow the NTFS/Windows file naming convention

Its quite often I reboot into Windows and decide to either do a data backup or play music while I work only to find out it cant access the folder, or read the files.  After which I have to reboot into Linux fix the error and go back again.

Tim

---

### Post by dcstar on 2011-04-20
> **lucast said:**
> Hi,

I am using NTFS on a partition that I share files between Ubuntu and Windows.  I have a problem for example when I rip music cd's, that quite often it puts characters in the filenames that Windows doesn't like e.g. a question mark or a fullstop at the end of a folder name.

**Is it possible to somehow configure either Ubuntu/gnome to not allow certain characters to be written to disk and throw up a warning**.  Basically I want to follow the NTFS/Windows file naming convention
........

No.

Linux apps are designed to use Linux filesystems, if you decide to use foreign filesystems then that's done at your own risk.

---

### Post by lucast on 2011-04-20
So there isn't a way to mount an NTFS drive to follow the Windows naming convention?

Tim

---

### Post by lucast on 2011-04-20
Looks like I may have found a possible solution with the NTFS-3g driver.  Not sure how to use this yet though.

**_Windows Filename Compatibility_**

NTFS supports several filename namespaces: DOS, Win32 and POSIX. While the ntfs-3g driver handles all of them, it always creates new files in the POSIX namespace for maximum portability and interoperability reasons. This means that filenames are case sensitive and all characters are allowed except ’/’ and ’\0’. This is perfectly legal on Windows, though some applications may get confused. The option windows_names may be used to apply Windows restrictions to new file names.

***windows_names***

This option prevents files, directories and extended attributes to be created with a name not allowed by windows, either because it contains some not allowed character (which are the nine characters ” * / : < > ? \ | and those whose code is less than 0×20) or because the last character is a space or a dot. Existing such files can still be read (and renamed).

---

### Post by WorMzy on 2011-04-20
That option isn't listed on the kernel documentation, but if it's a legitimate option, you can use it with the -o option when using the mount command, or by writing it in the options column in an fstab entry.

e.g.

```
sudo mount -t ntfs-3g -o uid=1000,gid=100,umask=002,windows_names /dev/sda2 /mnt
```

```
UUID=7A5C94995C94522D /mnt ntfs-3g auto,uid=1000,gid=100,umask=002,windows_names 0 0
```

---

### Post by lucast on 2011-04-20
Hi WorMzy,

It appears to work well.  I made the change in FSTAB and restarted the computer. 

```
UUID=4A10964610963941 /windows/d      ntfs-3g auto,windows_names 0 0
```

Mine now looks like the above.  The reason I took the UUID, GID and UMASK out is due to the fact I need to share this drive on my home network and I need Windows machines to be able to write to the disk.

I guess only time will tell if it works properly, but initial tests seem to say it does. :-D  I get an error message telling me the file name is not valid when I try and save a file e.g. T"i?m.txt

---

### Post by rygle on 2011-09-25
This new "windows_names" switch for NTFS-3G is something that a number of people campaigned for and convinced Tuxera to implement in May 2010. It is designed for exactly the reasons outlined by the OP in this post.

Here are more details;
[http://www.tuxera.com/forum/viewtopic.php?f=2&t=763](http://www.tuxera.com/forum/viewtopic.php?f=2&t=763)

In my opinion, this should be the default setup in Ubuntu.

---


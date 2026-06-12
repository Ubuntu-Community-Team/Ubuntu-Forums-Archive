---
title: "Disappearing Files"
date: 2010-04-16
forum: General Help
---

### Post by Torqradio on 2010-04-16
Ubuntu 10.04 Beta - 

I recently upgraded from 9.10. I have for some time been using an IOMEGA External drive, storing files created using Open Office. After I upgraded I continued to use those files and open them in OpenOffice 3.2. Yesterday I opened the drive to work on the files and the entire directory is missing. All the other directories seem to be there. Bizarre. Have tried using "locate" in the console, but the files are nowhere to be found. I tried accessing the permissions on the external drive but get the response "The permissions of IOMEGA HDD could not be determined".

Using a dual boot system with Windows Vista, booting through Grub.

I am a fairly new user.

I am frantic about getting the files back. Any help would be greatly appreciated.

Torq

---

### Post by cdenley on 2010-04-16
What kind of filesystem? Was it unmounted properly before the drive was disconnected or ejected? What kind of files (.odt, .doc, etc)?

---

### Post by Torqradio on 2010-04-16
Its an msdos file system. As to your question about unmounting, one of the first things I noticed on installing 10.04, was that the unmount command was not available in the right click menu for my external drive. Before that I always selected unmount, before removing it. The option "remove drive safely" was, so I used that command without unmounting when I wanted to unplug the drive, because the unmount option was no longer available.

The files are all .ods and .odt files.

I hope this sheds some light.

---

### Post by cdenley on 2010-04-16
Well, locate won't find any files on your external drive, since even if your filesystem was indexed while it was mounted, anything in /media should be ignored. If you want to search for your files in cased they were moved by accident, substitute /media/disk with your mount point:
```

find /media/disk -type f|grep -i "\.od[ts]"

```
If they were deleted by accident, check your trash or any hidden directories.
```

ls -d /media/disk/.

```
If they were actually deleted (not moved or moved to trash), you should be able to recover them with photorec from the testdisk package. Unless the deleted files have since been overwritten with new data. Have you been writing to the filesystem at all?

---

### Post by Torqradio on 2010-04-17
I used the find command, and made sure I got the syntax right. It wasn't able to find the file. The Drive is called Media/IOMEGA HDD in the file manager, but the console command seemed to be struggling with that syntax because it reported that it could not find "IOMEGA" or "HDD".

The result was as follows:

robacton@robacton-laptop:~$ find /IOMEGA HDD -type f|grep -i "\.od[ts]"
find: `/IOMEGA': No such file or directory
find: `HDD': No such file or directory
robacton@robacton-laptop:~$ find /media/IOMEGA HDD -type f|grep -i "\.od[ts]"
find: `/media/IOMEGA': No such file or directory
find: `HDD': No such file or directory
robacton@robacton-laptop:~$

The files weren't accidentally deleted, and aren't in the trash. How do I run the testdisk package and the photorec function?

Torqradio

---

### Post by cdenley on 2010-04-17
If your mount point has a space, you must enclose it in quotes. Arguments are separated by space, so it sees your mount point as 2 arguments, not 1.
```

find "/media/IOMEGA HDD" -type f|grep -i "\.od[ts]"

```
To use photorec:
```

sudo apt-get install testdisk
sudo photorec

```
However, if you're sure you always removed the drive "safely" and the files weren't deleted, you're wasting your time. Files don't delete themselves, so if they aren't there, then they probably never were, and perhaps your drive is failing.

---

### Post by Torqradio on 2010-04-17
Thanks for all the advice. I got photorec working. Forgot about the warning that you should have enough space on the drive you copy the rescued files to, and ran out of disk space, but after about 3 hours of continuos deleting while photorec ran, it found the files. I was able to recover 16 of the 17 missing files. I am ecstatic and still dont know how the stuff disappeared in the first place, but thanks for your patience.

As a separate issue: I first ran photorec in my normal user profile. The collections of files that it created were archived in my home directory. I found I couldn't delete these archives because I didn't have the necessary permissions. I stopped photorec and ran it again as a root user, and was able to delete the archives once I had checked them. I now need to change the permissions in my standard profile, from root, so that I can also delete those archives, but I cant find my standard home directory when I am logged on as a root user. Do you know how I go about finding it?

Torqradio

---

### Post by cdenley on 2010-04-17
> **Torqradio said:**
> Do you know how I go about finding it?
```

echo $HOME

```
It is /home/username by default. You can browse files as root with:
```

gksu nautilus

```

---

### Post by Torqradio on 2010-04-19
Thank you for all the help. I've found it and deleted the big files. I really appreciate the assistance.

Torqradio

---


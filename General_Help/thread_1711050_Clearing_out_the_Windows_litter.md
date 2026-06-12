---
title: "Clearing out the Windows litter"
date: 2011-03-20
forum: General Help
---

### Post by shade82000 on 2011-03-20
Hi everyone.

I made the complete switch nearly a year ago but I still have a very large collection of music and films on some secondary NTFS partitions that were  formatted in Windows XP years ago.

Most of the folders were created while I was using Windows and there are a large number of unwanted files left in EVERY folder that was there when Windows was installed.  These are files like DESKTOP.INI and THUMBS.DB which are a complete pain now as they are in 90% of the folders.

What would be the right command to search and destroy these files?  I'm a complete noob with terminal commands and someone suggested I run this command from the /media directory:

```
rm `locate desktop.ini`
```The problem is that the 'locate' command does not seem to look for anything in the /media directory or it's subdirectories.

Anyone know how to help me remove these files?

Thanks...

---

### Post by mikewhatever on 2011-03-20
You could use 'find' to search for and remove those files.

_example_
```
find /media/NTFS/ -name DESKTOP.INI -execdir rm {} \;
```

That command will search for 'DESKTOP.INI' files in /media/NTFS/ and remove them. Obviously, /media/NTFS/ is just an example, and your NTFS partitions will have different locations, also note that Linux is case sensitive, so that 'DESKTOP.INI' and 'desktop.ini' are not the same.

---


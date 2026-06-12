---
title: "Possibly Incorrect Hard Links on NTFS"
date: 2009-10-11
forum: General Help
---

### Post by robtoth on 2009-10-11
First post to ubuntu forums; hope my support question can be answered here!

I'm trying to use baobab to analyze my disk usage on /media/HD2, and for a certain directory, it says "0 items (contains hardlinks for 8.2GB)".  So I tried ```
ls -li
``` and this is the output:

```
212 -rwxrwxrwx 2 root root 366552510 2008-12-08 04:38 file 
```

I assume this means that another file is also pointing to this file.  The output of ```
fdupes -rH /media/HD2/
``` doesn't show anything.  The output of ```
find /media/HD2/ -xdev -inum 212
``` doesn't return anything other than file, as well the output of ```
find /media/HD2/ -samefile file
```

Not sure if this is helpful, but HD2 is an external usb hard drive of filesystem ntfs (automatically mounted).

Just trying to let baobab correctly analyze my hard drive :).  

Thanks in advance for your help.

---


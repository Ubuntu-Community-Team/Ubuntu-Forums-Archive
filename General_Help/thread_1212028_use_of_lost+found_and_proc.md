---
title: "use of lost+found and proc"
date: 2009-07-13
forum: General Help
---

### Post by dumblebee100 on 2009-07-13
well Its a while I have been using ubuntu and fedora ..

The filesystem is somewhat confusing for newbies ...

after some usage I came to know the usage of many folders under / 

but LOST+FOUND and /Proc ..they dont give me some basic meaning like devices or mount or media or libraries or boot
 
the folder proc takes nearly a GB ..so I want to know if that is really necessary ...but to my suprise I opened the folders in proc there are  many folders and many appear to be 0 byte files ..so what is the need of keeping empty files ....

my idea ..is to remove empty files( if that is safe )  and to know usage of all the folders under /

---

### Post by prshah on 2009-07-13
> **dumblebee100 said:**
> 
but LOST+FOUND and /Proc ..

the folder proc takes nearly a GB ..so I want to know if that is really necessary ...but to my suprise I opened the folders in proc there are  many folders and many appear to be 0 byte files ..so what is the need of keeping empty files ....

my idea ..is to remove empty files( if that is safe )  and to know usage of all the folders under /

lost+found contains "orphaned" and "lost" files, such as files recovered during a diskcheck (fsck). It is usually safe to delete file from this directory, but you may need root (sudo) permissions to do so.

"/proc" is a virtual filesystem; it does not really exist, and does not occupy space on the harddisk irrespective of what your file manager / disk usage utility shows. It is a representation of devices and their settings in your computer.

For example, if take a look at "/proc/kcore"```
ls -l /proc/kcore
``` you will find that it is equal to your installed and available memory. This file is a representation of your memory, and cannot be delete or altered in size, even with sudo; the only way to alter it is to PHYSICALLY change / remove the RAM modules installed on your board.

In summary:
/proc = hands off! (Except to modify settings when required)
/lost+found = usually safe to delete.

---

### Post by dumblebee100 on 2009-07-13
Thanks for the quick reply ...Have a nice day

---


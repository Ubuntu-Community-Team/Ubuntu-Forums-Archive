---
title: "Impossible to delete a file"
date: 2011-12-26
forum: General Help
---

### Post by Cecilio on 2011-12-26
I can not delete a file named "lenmus_lomse.layout.cbTemp". I also have removed all other content from the directory, renamed it (now is named "basura") and tried to remove the directory without success. Here is a log:

```
cecilio@pp1:/datos/USR/Desarrollo_wx/lenmus/build/basura$ ls
lenmus_lomse.layout.cbTemp
cecilio@pp1:/datos/USR/Desarrollo_wx/lenmus/build/basura$ rm -f *
cecilio@pp1:/datos/USR/Desarrollo_wx/lenmus/build/basura$ ls
lenmus_lomse.layout.cbTemp
cecilio@pp1:/datos/USR/Desarrollo_wx/lenmus/build/basura$ ls -il
total 36
301536 -rwxrwxrwx 1 root root 33079 2011-12-19 19:35 lenmus_lomse.layout.cbTemp
cecilio@pp1:/datos/USR/Desarrollo_wx/lenmus/build/basura$ 
cecilio@pp1:/datos/USR/Desarrollo_wx/lenmus/build/basura$ rm -i 301536
rm: cannot remove `301536': No such file or directory
cecilio@pp1:/datos/USR/Desarrollo_wx/lenmus/build/basura$ rm lenmus_lomse.layout.cbTemp 
rm: cannot remove `lenmus_lomse.layout.cbTemp': No such file or directory
cecilio@pp1:/datos/USR/Desarrollo_wx/lenmus/build/basura$ 
cecilio@pp1:/datos/USR/Desarrollo_wx/lenmus/build/basura$ sudo rm -i 301536
[sudo] password for cecilio: 
rm: cannot remove `301536': No such file or directory
cecilio@pp1:/datos/USR/Desarrollo_wx/lenmus/build/basura$ 
cecilio@pp1:/datos/USR/Desarrollo_wx/lenmus/build/basura$ sudo rm -f *
cecilio@pp1:/datos/USR/Desarrollo_wx/lenmus/build/basura$ ls
lenmus_lomse.layout.cbTemp
cecilio@pp1:/datos/USR/Desarrollo_wx/lenmus/build/basura$
cecilio@pp1:/datos/USR/Desarrollo_wx/lenmus/build/basura$ cd ..
cecilio@pp1:/datos/USR/Desarrollo_wx/lenmus/build$ rm -rf basura
rm: cannot remove directory `basura': Directory not empty
cecilio@pp1:/datos/USR/Desarrollo_wx/lenmus/build$
``` 

I don't know what else to do. Any help please?

I'm running a dual boot machine with Ubuntu 10.04 and Windows XP. To share data between both OSs I have a NTFS shared disk. Windows is rarely started, I normally run Ubuntu. The file to remove is on the NTFS volume. Was created in Ubuntu, having a Code::Blocks project open while googling for something. I don't know how the file was created. The file contains a valid PNG image that was in one of the visited pages. Is this a kind of malware?

Thank you
Cecilio

---

### Post by quickk on 2011-12-26
Did you try ```
sudo rm -rf basura
```  You can also try deleting it with nautilus by starting it with sudo:

```
gksudo nautilus
```

---

### Post by Cecilio on 2011-12-26
Thank you but ... nothing works!

```
cecilio@pp1:/datos/USR/Desarrollo_wx/lenmus/build$ sudo rm -rf basura
[sudo] password for cecilio: 
rm: cannot remove directory `basura': Directory not empty
cecilio@pp1:/datos/USR/Desarrollo_wx/lenmus/build$ 

```

Using nautilus generates the following error:

There was an error deleting lenmus_lomse.layout.cbTemp.
Error removing file: No such file or directory

I'm totally lost with this issue. More ideas?

Thanks,
Cecilio

---

### Post by guestolo on 2011-12-26
Is it possible there is a hidden file your not seeing?

In terminal change directory to 'basura' folder then run

ls -la

---

### Post by Howy on 2011-12-26
Seems like the file's information is corrupted. Have you tried running an fsck on the partition?

---

### Post by WorMzy on 2011-12-26
> **Howy said:**
> Seems like the file's information is corrupted. Have you tried running an fsck on the partition?

Since the file is on a NTFS partition, I'd rather recommend that OP boots into Windows and runs chkdsk on the affected partition.

It certainly seems to be some form of filesystem corruption to me too though.

---

### Post by Cecilio on 2011-12-27
> 
Originally Posted by **guestolo**
*Is it possible there is a hidden file your not seeing?*

There are no hidden files:

```
cecilio@pp1:/datos/USR/Desarrollo_wx/lenmus/build/basura$ ls -la
total 44
drwxrwxrwx 1 root root  4096 2011-12-24 19:10 .
drwxrwxrwx 1 root root  4096 2011-12-26 20:24 ..
-rwxrwxrwx 1 root root 33079 2011-12-19 19:35 lenmus_lomse.layout.cbTemp
```

> 
Originally Posted by **Howy**
*Seems like the file's information is corrupted. Have you tried running an fsck on the partition? *

I tried fsck but it ends with error:

```
cecilio@pp1:/datos/USR/Desarrollo_wx/lenmus/build/basura$ fsck /datos
fsck from util-linux-ng 2.17.2
fsck: fsck.ntfs-3g: not found
fsck: Error 2 while executing fsck.ntfs-3g for /dev/sda6
cecilio@pp1:/datos/USR/Desarrollo_wx/lenmus/build/basura$ 
```

> 
Originally Posted by **WorMzy**
*Since the file is on a NTFS partition, I'd rather recommend that OP boots into Windows and runs chkdsk on the affected partition.*

I started Windows and run chkdsk. It reported some errors in the index table and reported having removed the entry for file "lenmus_lomse.layout.cbTemp". Rebooting again to linux, I checked that the file was no longer there:  :D

```
cecilio@pp1:/datos/USR/Desarrollo_wx/lenmus/build/basura$ ls -la
total 8
drwxrwxrwx 1 root root 4096 2011-12-24 19:10 .
drwxrwxrwx 1 root root 4096 2011-12-26 20:24 ..
cecilio@pp1:/datos/USR/Desarrollo_wx/lenmus/build/basura$ 
```

And, finally, I removed the directory:

```
cecilio@pp1:/datos/USR/Desarrollo_wx/lenmus/build/basura$ cd ..
cecilio@pp1:/datos/USR/Desarrollo_wx/lenmus/build$ rmdir basura
cecilio@pp1:/datos/USR/Desarrollo_wx/lenmus/build$ ls
linux  msw2008  vsexpress  win32  win32_be
cecilio@pp1:/datos/USR/Desarrollo_wx/lenmus/build$ 

```

Thank you guys. I could not have solved this without your help.

Regards,  ):P
Cecilio

---


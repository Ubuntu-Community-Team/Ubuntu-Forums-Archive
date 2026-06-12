---
title: "Acces windows files in terminal"
date: 2009-09-07
forum: General Help
---

### Post by jeneverboy on 2009-09-07
Hi,

I want to acces the files I have in the windows partition with the terminal. If I go to places I can acces them so thats all normal. But I don't know how to acces the windows directory with the terminal.

I  know the basic commands like
```
cd \..
``` ```
dir
```

Thanks.

---

### Post by cholericfun on 2009-09-07
cd /media/"whatever_drive_windows_is_on"

might need to mount the drives first
(see myriads of other posts)

btw you typed \ which is windows style
not much use in linux

---

### Post by jeneverboy on 2009-09-07
OK, thanks.

I use
```
cd \..
```
to go to the directory above, its like the old DOS-command
```
cd ..
```
and it works.

---

### Post by Cato2 on 2009-09-07
The command line in Linux is similar but not identical.  Biggest point is that you use '/' not '\' within pathnames, and that '/' is the top of the whole tree, including drives mounted underneath '/', e.g. '/media/mydrive' might be another drive.

See [http://linuxcommand.gds.tuwien.ac.at/](http://linuxcommand.gds.tuwien.ac.at/) for a pretty good introduction to the command line.  Also google for 'linux tutorial shell'.

[http://www.yolinux.com/TUTORIALS/unix_for_dos_users.html](http://www.yolinux.com/TUTORIALS/unix_for_dos_users.html) is a handy table mapping from DOS/Windows to Linux.

[http://www.osalt.com/](http://www.osalt.com/) is great for finding apps corresponding to those you may use on Windows.

---


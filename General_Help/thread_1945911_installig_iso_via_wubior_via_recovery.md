---
title: "installig iso via wubi?or via recovery?"
date: 2012-03-23
forum: General Help
---

### Post by zombieonwar on 2012-03-23
hello, i am new to ubuntu and trying to install 11.4 version .
i have the iso image file..and how i can use it with wubi?
or shall i just install it from the recovery in my laptop?
will there be difference in installing from the recovery to from wubi...i tried to install it via wubi but as my internet connection is slow,i asked my friend to download the file..now i have the iso and confused if i can still install via wubi coz wubi still downloads the file...any help>>

---

### Post by bcbc on 2012-03-23
Unless you're running wubi from a CD, place wubi.exe and the ISO in the same directory before running Wubi.

1. Wubi.exe has to be the same release as the ISO (for 11.04 get it at the bottom of this page: [http://releases.ubuntu.com/11.04/](http://releases.ubuntu.com/11.04/))
2. The ISO has to be the desktop CD ISO (not alternate, or DVD ISO)

If it continues to download after you've done that, look in the %TEMP% directory for the log file and post that.

---


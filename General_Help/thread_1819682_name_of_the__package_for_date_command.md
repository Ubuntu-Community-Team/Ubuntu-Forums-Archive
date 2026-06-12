---
title: "name of the  package for date command"
date: 2011-08-06
forum: General Help
---

### Post by deniro on 2011-08-06
Hi
What is the name of the package for "/bin/date" command.
need to re-install
 
how can I determine that a spesific file belongs to which package?
 
using ubuntu 10.04 64bit
 
thx
deniro--

---

### Post by ~!geek!~ on 2011-08-06
Date command is there in the package Coreutils, 

You may reinstall it from command line by using command:

> sudo apt-get install coreutils 

---

### Post by scorp123 on 2011-08-06
> **deniro said:**
>  how can I determine that a spesific file belongs to which package? 

You can use the **dpkg -S /path/to/file** command for this. The name of the package will appear on the beginning of the line. Examples:

```
> dpkg -S /bin/date
coreutils: /bin/date

> dpkg -S /usr/bin/virtualbox 
virtualbox-4.1: /usr/bin/virtualbox

```

Once you know the name of the package you can check what files are in it using **dpkg -L NameOfPackage** .... 

```
> dpkg -L coreutils 
/.
/bin
/bin/cat
/bin/chgrp
/bin/chmod
/bin/chown
/bin/cp
/bin/date
/bin/dd
/bin/df
/bin/dir
/bin/echo
/bin/false
/bin/ln
/bin/ls
/bin/mkdir
/bin/mknod
/bin/mv
/bin/pwd
/bin/readlink
/bin/rm
/bin/rmdir
/bin/vdir
/bin/sleep
/bin/stty
/bin/sync
/bin/touch
/bin/true
/bin/uname
/bin/mktemp
...
```

---

### Post by deniro on 2011-08-06
I reinstalled the coreutils, that fixed the date command...
still there are some file under /bin which are corrupt.
 
also /var/lib/binfmts corrupt  too.
Tried  re-installing binfmts-support package but it didnt work for this one.
 
tried apt-get update/upgrade/dist-upgrade.. no luck repairing.
 
so I am  out of ideas...
 
I dont remember doing anything extraourdinary but this ubuntu system got corrupted
It was working one day, and logged out and next day everything screwed up.
 
does Ubuntu(10.04 64 bit) corruption kind of happens?  did anybody experienced similar? I never seen any other linux distro breaking like this with all bunch of corrupted file names. Why it did happen? again no idea
 
many filenames appear as gibberish letters and numbers and symbols under /bin and under /var/lib
 
Last, any points that I need to be aware of for this not happen again with the re-installation? I have to go through alot of setups that were working on the system.
 
thx
deniro--

---

### Post by scorp123 on 2011-08-06
Defective hard drive maybe? That's about the only thing that would cause such bad corruptions out of nowhere on a Linux system ...

---


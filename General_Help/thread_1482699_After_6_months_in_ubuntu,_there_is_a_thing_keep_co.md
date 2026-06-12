---
title: "After 6 months in ubuntu, there is a thing keep confusing me"
date: 2010-05-13
forum: General Help
---

### Post by vzhen on 2010-05-13
Hi,

if we install a software using deb package where is the "whole "program stored to ?

/usr/bin/xxx ?
/opt/xxx ?
but it is just 1 executable file. Where the other files?


What i mean the "whole program" is.....
If we download xxx.tar.gz and unzip. The unzipped folder is what i mean. 


Thanks in adv

---

### Post by kevin.krenz on 2010-05-13
I don't think the software necessarily installs to just one place - parts can end up in /opt, /etc, and so on. The .deb files are actually archived - you can extract them using "ar -x file.deb" if you're interested in looking at them a bit more in depth. There are a few different files that can be in there, including binaries, configuration files, some install-related scripts, and a control file that contains some information about dependencies. If you're using aptitude, the .deb files are stored in /var/cache/apt/archives by default.

---

### Post by gmargo on 2010-05-13
To find the files for an installed package, use the **dpkg(1)** command. For instance, here's the information for the **bash** package (for 8.04 Hardy):
```

$ dpkg -L bash
/.
/bin
/bin/bash
/etc
/etc/skel
/etc/skel/.bashrc
/etc/skel/.profile
/etc/skel/.bash_logout
/etc/bash.bashrc
/usr
/usr/share
/usr/share/doc
/usr/share/doc/bash
/usr/share/doc/bash/CHANGES.gz
/usr/share/doc/bash/NEWS.gz
/usr/share/doc/bash/INTRO.gz
/usr/share/doc/bash/POSIX.gz
/usr/share/doc/bash/README.Debian.gz
/usr/share/doc/bash/README.commands.gz
/usr/share/doc/bash/README.abs-guide
/usr/share/doc/bash/inputrc.arrows
/usr/share/doc/bash/copyright
/usr/share/doc/bash/FAQ
/usr/share/doc/bash/changelog.Debian.gz
/usr/share/doc/bash/COMPAT.gz
/usr/share/man
/usr/share/man/man1
/usr/share/man/man1/clear_console.1.gz
/usr/share/man/man1/rbash.1.gz
/usr/share/man/man1/bash.1.gz
/usr/share/man/man1/bashbug.1.gz
/usr/share/man/man7
/usr/share/man/man7/bash-builtins.7.gz
/usr/share/menu
/usr/share/menu/bash
/usr/bin
/usr/bin/bashbug
/usr/bin/clear_console
/bin/rbash
/bin/sh
diverted by dash to: /bin/sh.distrib
/usr/share/man/man1/sh.1.gz
diverted by dash to: /usr/share/man/man1/sh.distrib.1.gz

```If you have a .deb file that you wish to inspect, the proper tool to use is **dpkg-deb(1)** instead of **ar(1)**.

---

### Post by WorMzy on 2010-05-13
I believe that most things are installed to /usr/lib.

---

### Post by wojox on 2010-05-13
Yeah, they get dispersed to their respected homes. Nothing go's in /opt though unless you the admin put it there.

---

### Post by jerome1232 on 2010-05-14
The Linux Filesystem Hierarchy

[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

Every type of file has it's place in the file system, that link has a little overview of how it's all setup.

---

### Post by 3rdalbum on 2010-05-14
My screencast in my signature shows you how to find "where my installed program went".

---

### Post by vzhen on 2010-05-14
LOL,  i saw ur signature last time but my company blocks youtube and i forgot to bookmark your link.

Now i did, i will watch it later ^^.

Clear

Thanks guys.

---


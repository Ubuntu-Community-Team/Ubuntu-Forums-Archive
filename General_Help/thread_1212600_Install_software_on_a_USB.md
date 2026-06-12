---
title: "Install software on a USB"
date: 2009-07-13
forum: General Help
---

### Post by RedSingularity on 2009-07-13
How can i install software onto a USB in linux?  Even tho i have been using linux for some time now i have never done it.  I know in winblows it was as easy as choosing the install directory when the .exe was clicked.  Any help is appreciated.

---

### Post by t4thfavor on 2009-07-13
You may be able to do it with a command switch in apt-get. I would be that you may need applications that are compiled with all their dependancies statically linked so that they will run on machines that may not have them installed. 

I know when I compile stuff from source its as easy as copying the output of make to a directory of my choosing, even if its on a USB drive. So I know it is possible.

---

### Post by RedSingularity on 2009-07-13
In my case i am trying to install a .deb package to the USB drive so that i can move the USB drive to other linux systems and still use the software on the stick.

---

### Post by t4thfavor on 2009-07-13
look up commandline options for dpkg, theres probably an option for where to install it at.
```

--admindir=<directory>     Use <directory> instead of /var/lib/dpkg.
  --root=<directory>         Install on a different root directory.
  --instdir=<directory>      Change installation dir without changing admin dir.

```

---


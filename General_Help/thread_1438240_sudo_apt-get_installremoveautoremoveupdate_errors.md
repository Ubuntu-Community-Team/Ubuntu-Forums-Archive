---
title: "sudo apt-get install/remove/autoremove/update errors"
date: 2010-03-24
forum: General Help
---

### Post by RuhiWarrior19 on 2010-03-24
I failed to install the packages limewire-basic and ttf-mscorefonts-installer a while back. That is not what I am concerned about, but now whenever I run an apt-get command it tries to process these files again. It tells me:

> Setting up limewire-basic (5.5.7-1) ...
Warning: /usr/share/gconf/schemas/limewire.schemas could not be found.
Usage: gconf-schemas --[un]register file1.schemas [file2.schemas [...]]

gconf-schemas: error: You need at least a file to (un)register.
dpkg: error processing limewire-basic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up ttf-mscorefonts-installer (3.0) ...


and at the end I get this error:

> All done, no errors.
arial32.exe: FAILED
sha256sum: WARNING: 1 of 1 computed checksum did NOT match
Checksum mismatch for arial32.exe, aborting!
dpkg: error processing ttf-mscorefonts-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 limewire-basic
 ttf-mscorefonts-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)


also, many of my installs have been failing to fetch some archives and telling me:
> E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?


--fix-missing always works, but I am worried it is happening often because of an underlying problem.

This is a brand new install of 9.10 on an Asus eepc 1005HAB.

Any help would be awesome. I would prefer to learn how to fix this all in the terminal, but if graphical stuff is easier to explain I would love to have the help.

Love,
Gerald

---

### Post by kerry_s on 2010-03-24
first try purgeing that messed up crap.

```
sudo apt-get --purge limewire-basic ttf-mscorefonts-installer
```

---

### Post by RuhiWarrior19 on 2010-03-24
I actually got the ttf-mscorefonts-installer removed by doing a complete removal from synaptic, but that doesn't work for limewire-basic.

When I try sudo apt-get --purge limewire-basic
 it tells me E: Invalid operation limewire-basic

---


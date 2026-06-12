---
title: "dpkg: error ... Help!!!!!!!!!"
date: 2006-02-08
forum: General Help
---

### Post by maqi on 2006-02-08
Hi all,

I have been using revelation password manager for some time. In order to have the most current version I have been downloading the latest version from the developer as a .tar.bz2. I extract then run ./configure -all good. I then run checkinstall, satisfy any -dev package requirements and rerun checkinstall. This produces a deb package which is installed via dpkg -i.

This has worked fine until recently. I updated revelation and tried installing with dpkg -i. I get the following error whenever I try to do this:

```
dpkg: error processing revelation_0.4.x-1_i386.deb (--install):
 trying to overwrite `/usr/share/applications/mimeinfo.cache', which is also in package capplets-data
```

The exact version number seems to make no difference. The worst thing is that I cannot go back to the previous (working) version of revelation - I still encounter the same error :(

Any help would be greatly apprecitated - I have googled to no avail. I have searched these forums to no avail. At the moment I am unable to access my passwords. I'm just glad I paid my bills BEFORE I tried to upgrade!!!!

---

### Post by RAOF on 2006-02-08
There are two easy solutions:
1) You can remove the capplets-data package - that should prevent the conflict.  However, you may **want** the capplets-data ;)
2) You can install the .deb with "dpkg --install --force-overwrite thedeb.deb".  This will ignore that error, and force dpkg to overwrite the file.  This is probably the better option, although it may still make things not quite work.

---

### Post by maqi on 2006-02-08
Hey RAOF,

Doh!!! I didn't even think to use --force-overwite. That worked perfectly. Thanks heaps for the tip. If capplets starts acting weird on me I'll know how the problem started ... and try a reinstall of that :)

Cheers,
maqi :)

---


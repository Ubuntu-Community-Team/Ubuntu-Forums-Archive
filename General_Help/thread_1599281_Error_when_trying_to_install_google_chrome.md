---
title: "Error when trying to install google chrome"
date: 2010-10-17
forum: General Help
---

### Post by ww711 on 2010-10-17
I'm currently trying to install google chrome via the command line, for a ubuntu 10.10 from an upgraded 10.04.

```
sudo dpkg -i google-chrome-stable_current_i386.deb 
```

I get the below output.

```
warning, in file '/var/lib/dpkg/available' near line 38112 package 'virtualbox-3.0':
 error in Version string '3.0.12-54655_Ubuntu_karmic': invalid character in revision number
dpkg: error processing google-chrome-stable_current_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 google-chrome-stable_current_i386.deb
```

I've browsed to the file and line number, but unsure what to remove and where to start deleting or commenting out the code from.

Any thoughts?

---


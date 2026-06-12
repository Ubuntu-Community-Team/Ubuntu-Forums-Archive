---
title: "making a live cd"
date: 2010-09-09
forum: General Help
---

### Post by cry8wolf9 on 2010-09-09
ok i downloaded the ubuntu-10.04.1-desktop-i386.iso and i have the APTonCD program to make the cd. But i was wondering if thee is a script to redownload all the packages ive installed on the system? i usally keep my APT clean so i have nothing in the folder to use

---

### Post by nothingspecial on 2010-09-09
```
dpkg --get-selections
```

will tell you what you have installed on your system

---

### Post by cry8wolf9 on 2010-09-09
i know whats installed on the system its just that id like to redownload all of the packages so i can add them to the cd is there a program or command for that?

---

### Post by NearlyALaugh on 2010-09-10
Check out Remastersys:

[http://en.wikipedia.org/wiki/Remastersys](http://en.wikipedia.org/wiki/Remastersys)

---

### Post by john newbuntu on 2010-09-10
If you open synaptic package manager, choose "installed" on the left panel, and then Ctrl-A on the right panel, this will select all installed packages.  Right click and mark for re-installation.  Then on the "File" menu, there is a "Generate Package Download script" option.  Choose that and give it a name. Hit OK.  You should find a script that uses wget to download all installed packages in the system.

---


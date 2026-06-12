---
title: "Khelpcenter in Dapper"
date: 2006-05-04
forum: General Help
---

### Post by nejode on 2006-05-04
Khelpcenter only generates the index for man pages, and when you try to build the index for the KDE apps manual, it spits out the following error message in the details box:

X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
INDEXDIR: /home/nelson/.kde/share/apps/khelpcenter/index/
FINDCMD: find /usr/share/doc/kde/HTML/en/ -name index.docbook
Creating index for 'kde_application_manuals'
htdig failed 

You can always look up what you want manually in the contents tab, but the find function only gives out UNIX man pages.  I know almost nobody uses the helpcenter, but I look up there for info on KDE apps before hitting the web.

Anybody have any idea about this bug.  Thanks beforehand.

---

### Post by Parkotron on 2006-05-04
This has bothered me for quite a while, as well. I've yet to find a fix.

---

### Post by magnusbb on 2006-05-05
I am using Breezy, but I think this solution will work fine in Dapper too.

Just apt-get the package "htdig", and try doing the index generating again.

A "whatis" of the package gives me "retrieve HTML documents for ht://Dig search engine".

---

### Post by nejode on 2006-05-05
[QUOTE=magnusbb]I am using Breezy, but I think this solution will work fine in Dapper too.

Just apt-get the package "htdig", and try doing the index generating again.

A "whatis" of the package gives me "retrieve HTML documents for ht://Dig search engine".[/QUOTE]



A truckload of thanks magnusbb!!  It's working fine right now.  Apt-get recomends a few other packages, I'm going to install themn to see what up.... ( you helped out Parkotron at the same time too!).... regards...

---


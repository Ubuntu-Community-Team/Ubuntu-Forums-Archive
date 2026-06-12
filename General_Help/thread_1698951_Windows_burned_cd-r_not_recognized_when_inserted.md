---
title: "Windows burned cd-r not recognized when inserted"
date: 2011-03-03
forum: General Help
---

### Post by Sefianix on 2011-03-03
I'm running 64-bit Kubuntu (10.04.2 LTS).  I have CD-Rs burned from work from a Windows machine (with Sonic?).  I think they are multisession disks.  Most other disks get recognized by my comp except for these.  It's really annoying that these discs don't get recognized.  I've managed to sudo mount a disc.  I can read the disc after that.

output of isoinfo -d -i /dev/cdrom:
CD-ROM is in ISO 9660 format
System id: 
Volume id: 100926_1540
Volume set id: 
Publisher id: 
Data preparer id: 
Application id: 
Copyright File id: 
Abstract File id: 
Bibliographic File id: 
Volume set size is: 1
Volume set sequence number is: 1
Logical block size is: 2048
Volume size is: 178273
Joliet with UCS level 1 found
NO Rock Ridge present


**Anyone have any ideas how I can make these discs immediately recognizable in my desktop?**  I have lots of discs to check (and more in the future).  Some I need to duplicate.  K3b won't read them correctly either.  (they sometimes show in K3b with short/garbled filenames.)  I don't want to sudo mount and umount each one.

Thanks

---


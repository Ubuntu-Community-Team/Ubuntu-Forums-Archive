---
title: "Need help grub messed up windows"
date: 2011-05-31
forum: General Help
---

### Post by Ericthegreat on 2011-05-31
So I installed 11.04 but then there was no grub so I could only boot to windows (worked fine) so then I installed plop boot manager (windows still booted)and then booted my linux partition and grub decided to take over as boot manager, now nothing can boot windows and ubuntu will only boot 50% of the time, windows repair utility cannot see my partitions (nor can gparted live cd ect, but I know they are there cause linux sometime boots) chkdsk /(whatever) says disk write protected sfc says it is schedualed for repair, I been trying to fix this for hours, I could really use some help tyvm in advance sorry for grammer.

---

### Post by garvinrick4 on 2011-05-31
No way to know even what format windows is and or what is in grub when trying multiple ways of installing to mbr. Have to Download this Script to Desktop in Linux and run this
command in Terminal will make a RESULTS text file copy and paste here.
[SourceForge.net: Boot Info Script - Project Web Hosting - Open Source Software]("http://bootinfoscript.sourceforge.net/") 
```
 sudo bash [path/to/the/download_folder]/boot_info_script.sh
```

Can use a install cd for Ubuntu using Try Ubuntu with internet connection to do
this also.

---

### Post by Ericthegreat on 2011-06-01
[http://pastebin.com/C5qRfk7s](http://pastebin.com/C5qRfk7s)

posted here was too big

seems pc thinks /dev/sda1 and /dev/sda3 is the same

---


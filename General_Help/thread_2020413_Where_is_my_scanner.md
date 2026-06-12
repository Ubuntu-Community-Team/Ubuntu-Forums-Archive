---
title: "Where is my scanner?"
date: 2012-07-08
forum: General Help
---

### Post by Lloydb39 on 2012-07-08
Just not my day, I guess. I have an Epson 4490 scanner hooked up to my Dell running Ubuntu 11.10. SANE says "found USB scanner (vendor=0x04b8, product=0x0119) at libusb:001:003
found USB scanner (vendor=0x050d, product=0x845a) at libusb:001:002"
However, that is as far as I can get. Old thread says I need iscan but I went to that page and ran around in circles. It told me what deb I need but could not find where to download it from. Thought I could sudo it from Terminal but that didn't work either.
Anyone have a tip on how to get this sucker running? Thanks.

---

### Post by Lloydb39 on 2012-07-08
Update: Found the deb but can't install:
 sudo dpkg -install iscan-plugin-gt-x750_2.1.2-1_i386.deb
dpkg: error: unknown option -n

Type dpkg --help for help about installing and deinstalling packages 
[*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Anyone?

---

### Post by krustenBrot on 2012-07-08
> dpkg --helpgives the answer - 
first line:> 
Commands:
 -i  |  --install       <.deb file name> ... | -R|--recursive <directory> ...try:```

sudo dpkg --install iscan-plugin-gt-x750_2.1.2-1_i386.deb
```or:
```
sudo dpkg -i iscan-plugin-gt-x750_2.1.2-1_i386.deb
```

---

### Post by Lloydb39 on 2012-07-08
I get "no such file or directory" but it is in my download folder

---

### Post by krustenBrot on 2012-07-08
Have you tried simply double clicking it and install it via the **Ubuntu Software Center**?

Have you given the whole path or switched to your Downloads Folder with **cd**?
 Just type **cd /directory/where/thedebis** for example *cd /home/Krustenbrot/Downloads*

**plus:** did you know you can *auto-complete* entries with the [**TAB**] key?

---

### Post by Lloydb39 on 2012-07-08
> **krustenBrot said:**
> Have you tried simply double clicking it and install it via the **Ubuntu Software Center**?

Have you given the whole path or switched to your Downloads Folder with **cd**?
 Just type **cd /directory/where/thedebis** for example *cd /home/Krustenbrot/Downloads*

**plus:** did you know you can *auto-complete* entries with the [**TAB**] key?
  Very helpful. Thank you! I now have a scan icon, but unfortunately, it can't find the scanner, which is on, plugged in and working. Not sure what to do next but I think I'll try system info to see if it knows where it is.

---

### Post by krustenBrot on 2012-07-10
Have you tried **simpleScan?  **Just an idea - i had a similair problem with my girlfriend it worked out with simpleScan. You may wanna give it a try.
It shoud be preinstaled - oben up the **Dash** (*Super key*) type in **simpleScan** launch it and try

---


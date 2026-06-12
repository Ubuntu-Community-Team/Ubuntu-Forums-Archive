---
title: "Need help installing printer"
date: 2010-02-12
forum: General Help
---

### Post by altjx on 2010-02-12
I've downloaded 2 cupswrapper drivers just in case I missed one, I got them both from [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-290C](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-290C) which includes 2 cupswrapper drivers... I tried the following commands
```
sudo aa-complain cupsd
sudo mkdir /usr/share/cups/model
sudo ln -s /etc/init.d/cupsys /etc/init.d/lpd
sudo mkdir /var/spool/lpd
sudo apt-get install csh sane-utils
sudo dpkg -i cupswrapper driver deb 1.1.2-2

```

however, this is the error i get
```
alton@alton-laptop:~$ sudo dpkg -i mfc290ccupswrapper-1.1.2-2.i386.deb 
Selecting previously deselected package mfc290ccupswrapper.
(Reading database ... 146660 files and directories currently installed.)
Unpacking mfc290ccupswrapper (from mfc290ccupswrapper-1.1.2-2.i386.deb) ...
dpkg: dependency problems prevent configuration of mfc290ccupswrapper:
 mfc290ccupswrapper depends on mfc290clpr; however:
  Package mfc290clpr is not installed.
dpkg: error processing mfc290ccupswrapper (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mfc290ccupswrapper

```

That's with the .deb and when I try with the .rpm, I get 
```
alton@alton-laptop:~$ sudo dpkg -i mfc290ccupswrapper-1.1.2-2.i386.rpm 
dpkg-deb: `mfc290ccupswrapper-1.1.2-2.i386.rpm' is not a debian format archive
dpkg: error processing mfc290ccupswrapper-1.1.2-2.i386.rpm (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 mfc290ccupswrapper-1.1.2-2.i386.rpm
```

---

### Post by altjx on 2010-02-12
[FONT=Arial Narrow]nvm, i had to force it[/FONT] using the 
Command (for  dpkg)  :  dpkg  -i  --force-all  (cupswrapper-drivername)
command

---

### Post by altjx on 2010-02-12
Ok, although I added the printer as MFC290, it's not printing anything...

---

### Post by tcchris on 2010-02-12
Did this work ?
I usually install the lpr driver , and then the cups driver
Both are on the Brother website .
The lpr driver was the dependancy you did not have

---

### Post by altjx on 2010-02-12
> **tcchris said:**
> Did this work ?
I usually install the lpr driver , and then the cups driver
Both are on the Brother website .
The lpr driver was the dependancy you did not have

Would I need the rpm's or the deb files?

---

### Post by altjx on 2010-02-12
Gotcha, installed the LPR and CUPS and now it's working. Thanks man =)

---

### Post by tcchris on 2010-02-12
Deb for Ubuntu
Brother has very good documentation for installing .
Read through what pertains to your printer and OS carefully .
It sounds like you have done the preliminaries 
So , install lpr , install cups driver , 
Mine is networked , so I have to edit a file and edit the printer in cups .
All of that is documented at brother
If you are connected usb , then after installing the two drivers I think it will just work

---

### Post by tcchris on 2010-02-12
Enjoy !!

---


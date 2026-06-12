---
title: "Brother j615w Ubuntu 10.10 64-bit driver"
date: 2011-03-08
forum: General Help
---

### Post by gypsumwolf on 2011-03-08
I am looking for a way to install the driver for Brother j615w on Ubuntu 10.10 64-bit. There is a 32-bit driver on their website:

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-J615W]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-J615W")

---

### Post by metalf8801 on 2011-03-08
I take it when you go to 
System > Administration > Printer 
You don't see your printer listed? 

I've found that Ubuntu often just finds the printer and works with it. 

Also see this link [https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)

Good luck 
Dan

---

### Post by plucky on 2011-03-08
> **gypsumwolf said:**
> I am looking for a way to install the driver for Brother j615w on Ubuntu 10.10 64-bit. There is a 32-bit driver on their website:

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-J615W]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-J615W")

From the Brother website
> 
# Pre-required Procedure (5)
    Related distributions
    Debian 64 bit version, [COLOR="Blue"]Ubuntu 64 bit version[/COLOR]
    Related products/drivers
    printer/PC-FAX drivers
    Requirement
    [COLOR="Red"]ia32-libs or lib32stdc++ is required to be installed.[/COLOR]

My 64-bit system has both installed,but I am on 10.04 and my printer works.


Good Luck

---

### Post by gypsumwolf on 2011-03-08
I have ia32-libs and lib32stdc++ installed.

It will not let me install the driver from the brother website because wrong architecture type.

If I go to printers > Network > Find, the printer is found then it asks for a driver which I do not have.


....maybe i will just need to use 32-bit Ubuntu...?

---

### Post by walt.smith1960 on 2011-03-08
> **gypsumwolf said:**
> I have ia32-libs and lib32stdc++ installed.

It will not let me install the driver from the brother website because wrong architecture type.

If I go to printers > Network > Find, the printer is found then it asks for a driver which I do not have.


....maybe i will just need to use 32-bit Ubuntu...?

Nothing that dramatic I think. From Brother's web site:

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn3.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn3.html)
```
Command (for dpkg)  :  dpkg  -i  --force-all  (lpr-drivername)
```. Brother only releases 32 bit linux drivers but using the --force-all switch seems to make the 32 bit drivers work fine on 64 bit O.S.s  I've had to do the same thing when installing Brother printers not found in the Foomatic database on a 64 bit installation.  There's a trick I've found when having to enter file names at the command line.  Capital letters, spaces and punctuation must all be perfect.  I open a terminal type the command(s) then copy & paste the file name rather than type it.  I've had better luck that way.

---

### Post by gypsumwolf on 2011-03-08
```

root@:/media/Jupiter/Downloads# dpkg  -i  --force-all mfcj615wlpr-1.1.1-1.i386.deb
dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
Selecting previously deselected package mfcj615wlpr.
(Reading database ... 229370 files and directories currently installed.)
Unpacking mfcj615wlpr (from mfcj615wlpr-1.1.1-1.i386.deb) ...
Setting up mfcj615wlpr (1.1.1-1) ...
mkdir: cannot create directory `/var/spool/lpd/mfcj615w': No such file or directory
chown: cannot access `/var/spool/lpd/mfcj615w': No such file or directory
chgrp: cannot access `/var/spool/lpd/mfcj615w': No such file or directory
chmod: cannot access `/var/spool/lpd/mfcj615w': No such file or directory
root@:/media/Jupiter/Downloads# cd /var/spool/
root@:/var/spool# mkdir lpd
root@:/var/spool# cd lpd/
root@:/var/spool/lpd# mkdir mfcj615w
root@:/var/spool/lpd# cd /media/Jupiter/Downloads/
root@:/media/Jupiter/Downloads# dpkg  -i  --force-all mfcj615wlpr-1.1.1-1.i386.deb
dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 229392 files and directories currently installed.)
Preparing to replace mfcj615wlpr 1.1.1-1 (using mfcj615wlpr-1.1.1-1.i386.deb) ...
Unpacking replacement mfcj615wlpr ...
Setting up mfcj615wlpr (1.1.1-1) ...
root@:/media/Jupiter/Downloads# dpkg  -i  --force-all mfcj615wcupswrapper-1.1.1-1.i386.deb
dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
Selecting previously deselected package mfcj615wcupswrapper.
(Reading database ... 229392 files and directories currently installed.)
Unpacking mfcj615wcupswrapper (from mfcj615wcupswrapper-1.1.1-1.i386.deb) ...
Setting up mfcj615wcupswrapper (1.1.1-1) ...
cups start/running, process 13562


```

When it finds the printer i need to use the dnssd one, not the other one on the list. It works! Thanks!

---

### Post by walt.smith1960 on 2011-03-09
Great!! If it works don't mess with anything.  I've had two issues with Brother printers that you may just keep in mind in case they surface for you.  I have two networked MFC models.  One problem that I had encountered in the past was a "printer not found" message.  My solution for that was to open printer properties and change the device URI to :```
socket://192.168.x.xxx:9100
``` inserting your printer's I.P. address in place of the xxx. This has been quite reliable for me.  The second issue was with an older model MFC-7820N.  It was *painfully* slow, especially when printing multiple pages.  The driver choices were BRscript, Foomatic driver and recently a CUPS driver.  The CUPS driver works MUCH better & faster than the other two choices.  I think I found the CUPS driver in synaptic.

---


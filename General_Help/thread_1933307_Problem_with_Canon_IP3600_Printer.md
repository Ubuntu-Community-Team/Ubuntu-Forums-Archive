---
title: "Problem with Canon IP3600 Printer"
date: 2012-02-29
forum: General Help
---

### Post by silviutp on 2012-02-29
I have problems printing with a Canon IP3600 Printer.
The drivers that I've found for it :
'Canon PIXMA iP3000 - CUPS+Gutenprint v5.2.7 Simplified '
When I look in the CUPS server page I don't see any problem with the installed printer. Also when I try to print a test page the server says the printing was ok but the printer doesn't print, only blinks a LED few times... 

The printer is fine on another computer with Windows.

I'm using Ubuntu 11.10 /  x86_64.

Thank you.

---

### Post by habana on 2012-02-29
I have similar problems with a Canon iP3300. Worked fine with 11.04 32 bit. No go with 11.10 32 bit. Printer works fine with a Windows PC using the same cable. If a try a test page, the printer LED blinks but nothing else happens. If I try to print a document I get a message saying the document is printing and a few seconds later a message saying the document has printed. The printer LED does not blink. The log files look OK. The same USB port works fine with other devices.

The files I needed to get it to work with 7.10 and later were

cnijfilter-common_2.70
cnijfilter-ip3300_2.70

I do recall an issue with CUPS a couple of years ago. I had to rename a cupsys file or somesuch. After that, no problem until 11.10

---

### Post by aikishugyo on 2012-03-09
> **silviutp said:**
> I have problems printing with a Canon IP3600 Printer.
The drivers that I've found for it :
'Canon PIXMA iP3000 - CUPS+Gutenprint v5.2.7 Simplified '
When I look in the CUPS server page I don't see any problem with the installed printer. Also when I try to print a test page the server says the printing was ok but the printer doesn't print, only blinks a LED few times... 

The printer is fine on another computer with Windows.

I'm using Ubuntu 11.10 /  x86_64.

Thank you.

You probably need to use the iP3600 driver. Since gutenprint has been developed quite a bit since 5.2.7, if you install the latest 5.2.8pre1 you should have better support for various options.

---

### Post by silviutp on 2012-03-09
Do you know if are there any deb packages for 5.2.8pre1 ?

---

### Post by 2CV67 on 2012-03-09
This might be worth a try:
[http://ubuntuforums.org/showpost.php?p=11704448&postcount=5](http://ubuntuforums.org/showpost.php?p=11704448&postcount=5)

> I would like to know more of the background, but it looks as though one Michael Gruz has set up a PPA which allows you to install a huge range of Canon drivers via Synapt, which WORK - just like that!

---

### Post by habana on 2012-03-09
Yea! That fixed it. Thanks 2CV67 and thanks to Michael Cruz

---

### Post by silviutp on 2012-03-14
> **aikishugyo said:**
> You probably need to use the iP3600 driver. Since gutenprint has been developed quite a bit since 5.2.7, if you install the latest 5.2.8pre1 you should have better support for various options.

It worked after installing 5.2.8pre1. 
These are the steps that I've followed
I've downloaded the source files from here :[https://launchpad.net/ubuntu/+source/gutenprint/5.2.8~pre1-0ubuntu1](https://launchpad.net/ubuntu/+source/gutenprint/5.2.8~pre1-0ubuntu1)

#./configure --prefix=/usr

# make
I've installed some dev packages after I had an error when compiling
# sudo apt-get install libgnomecups1.0-dev libcups2-dev  libcupscgi1-dev libcupsdriver1-dev libcupsimage2-dev libcupsmime1-dev libcupsppdc1-dev
I don't know if all of them are needed.
# make
# sudo make install
# sudo /etc/init.d/cups restart
I've edited the printer configuration from CUPS interface and selected the new drivers for my IP3600 printer and now it works.
Thank you!!

---


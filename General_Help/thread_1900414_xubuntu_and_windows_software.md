---
title: "xubuntu and windows software"
date: 2011-12-26
forum: General Help
---

### Post by Max_Max on 2011-12-26
Hi i am an absolute newcomer to linux. I want to use a bootable Desktop-CD of xubuntu (10.04 lucid Lynx°) to scan an old windows version for malware and create an iso image of the hard diisk content.

I wanted to use Malwarebytes anti-malware and img burn. It didn't work, of course. Iread somewhere that over an application called "wine" windows software can be used under linux.

Its ought to be included in the newest ubuntu version, but how about xubuntu? (I have to use it because of the lower system requirements)Is there another version* I could use? Can I "upgrade" it somehow?

Or should i use different software? (other than Malwarebytes and Img. burn)   

Thanks for the help, and excuse my lack of knowledge.

---

### Post by Topsiho on 2011-12-26
If you can find wine in the repositories, or can install it in a terminal (sudo apt-get install wine) then wine can be used in xubuntu too.

Wine however is not perfect. Some Windows programs can be run using wine, and many can not. Just try it.

Good luck, and a good X-Mas to every one :)

Topsiho

---

### Post by snowpine on 2011-12-26
Wine runs fine in Xubuntu, however, you should visit [http://winehq.org](http://winehq.org) and check their App Database to see if the apps you need are actually supported.

Linux has its own malware/virus/disk utility/etc. applications that run natively and do not require wine. If you check the Sticky thread at the top of the Security subforum you'll find some good suggestions.

---

### Post by sdowney717 on 2011-12-26
Avast antivirus has a linux version
[http://www.avast.com/linux-home-edition](http://www.avast.com/linux-home-edition)

image hard drive linux
[http://www.google.com/search?ix=hca&sourceid=chrome&ie=UTF-8&q=image+hard+drive+linux](http://www.google.com/search?ix=hca&sourceid=chrome&ie=UTF-8&q=image+hard+drive+linux)

typically better to use native tools and abandon windows completely

---

### Post by Myrddin Emrys on 2011-12-26
> **Max_Max said:**
> Hi i am an absolute newcomer to linux. I want to use a bootable Desktop-CD of xubuntu (10.04 lucid Lynx°) to scan an old windows version for malware and create an iso image of the hard diisk content.

I'd suggest a dedicated antivirus live CD for the malware scan, like Avira's Linux-based rescue system:

[http://www.avira.com/en/support-download-avira-antivir-rescue-system](http://www.avira.com/en/support-download-avira-antivir-rescue-system)

---

### Post by Max_Max on 2011-12-27
Thanks for the help so far. Unfortunaly i can't use the Avira rescue-cd due to system requirements (my laptop only has 256 mb RAM and an old 2,2 GHz Pentium processeur)I tried the system rescue-cd ,avalabile under partimage, too. Same result.

Anyway, xubuntu works fine. As far as wine is concerned i'd rather not wamt to connect my Laptop to the Internet. Last time i did that, part of my windows system data disapeared.(I typed in the sudo command for wine and it says i don't have enough space in var/cache apt/archive...)

Where is additional software installed? Since I am runnung a Live CD I would rather want it to be installed to a flash drive than to my corrupted hard disk.

I downloaded avast4worstation (deb) and partimage (tar.bz2), as recommended. How can I run them from the flash drive? 

I would be realy gracious for a step by step guide.   

Thanks a lot again.

---

### Post by Topsiho on 2011-12-28
Hello Max_Max,

Nice to read you have succeeded installing Xubuntu on your laptop (256 MB is indeed too little for Ubuntu itself, that needs > 511 MB).

Without internet however there is not so much fun to be had. First thing to do, using internet, is updating xubuntu, for security reasons and for program updates (most applications are maintained continuously, drivers for new hardware are made available in newer kernels, and so on). Running Linux you need not be afraid that data get lost without you doing it yourself.

The binaries (executables) of applications you install are stored in /bin or in /sbin, the configurations in /etc (most are human readable and editable files), and your personal settings in your /home map (/home/max_max or whatever). Just try and have  a look : Places/Computer/Filesystem (or words like this, I (re)translate from Dutch :)

As for running (x)ubuntu from a flashdrive, just google for it and take your pick :)

Topsiho

---

### Post by Max_Max on 2011-12-29
Since I almost tried every rescue CD out there, and xubuntu just always is hangs itself during the instalation process of Avast, I decided to give damn small Linux a shot and downloaded Avast again... 

The path is ramdisk/home/dsl/avast4workstation_1 3 0-2_i386.  
(I can't find it under "MyDSL" so I can't just click on Install)

Can somebody tell me what to type into the terminal? 

Thanks again. :)

---


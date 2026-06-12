---
title: "problem creating deb file with alien"
date: 2010-11-19
forum: General Help
---

### Post by shanzabar on 2010-11-19
Hey, I'm running a fresh install of ubuntu 10.10 and was having trouble finding a suitable wireless driver for my dell studio 1535. By default it wants to install the broadcom STA wireless driver, which after research I found didn't work with this model. So I went to dell's website and got the driver from them directly. The file they gave me was an .RPM file.

 My problem is as follows:

I placed the rpm on the desktop and installed alien. using the terminal I attempted the convert using

~/Desktop$ sudo alien -k tg3-3.85k-1.src.rpm

the terminal reports to me that the .deb file is created (I see it on the desktop) but then almost immediately it's deleted. It's not hidden...

It's probably something simple, but I'm too much of a noob to figure it out. =/

any suggestions?

---

### Post by dino99 on 2010-11-19
follow this howto:

[https://help.ubuntu.com/community/RPM/AlienHowto](https://help.ubuntu.com/community/RPM/AlienHowto)

---

### Post by shanzabar on 2010-11-19
> **dino99 said:**
> follow this howto:

[https://help.ubuntu.com/community/RPM/AlienHowto](https://help.ubuntu.com/community/RPM/AlienHowto)

I've done that before, it doesn't work.

when I try alien -i the deb file is created, but then it's deleted so I get:

tg3_3.85k-1_amd64.deb generated
error processing tg3_3.85k-1_amd64.deb (--install):
 cannot access archive: No such file or directory

---

### Post by sikander3786 on 2010-11-19
> **shanzabar said:**
> I've done that before, it doesn't work.

when I try alien -i the deb file is created, but then it's deleted so I get:

tg3_3.85k-1_amd64.deb generated
error processing tg3_3.85k-1_amd64.deb (--install):
 cannot access archive: No such file or directory
Which version of Ubuntu have you installed? 64-bit?

---

### Post by shanzabar on 2010-11-19
> **sikander3786 said:**
> Which version of Ubuntu have you installed? 64-bit?

that did it. I thought I had both 32 and 64 in the same directory when I made the bootable flash drive to install it. when it autodetects what .iso to use, it chose 32...I didn't even check until you said something.

I knew it was something simple, man I fail. 


thank you!

---

### Post by sikander3786 on 2010-11-19
> I thought I had both 32 and 64 in the same directory when I made the bootable flash drive to install it. when it autodetects what .iso to use, it chose 32...I didn't even check until you said something.


I've never heard of that before. You need to create the USB for 32-bit or 64-bit individually, whatever you prefer. But I don't know how can you put both the ISOs on the same USB? The installer only detects if the system has more than 3 GB or RAM and installs the PAE-kernel if needed to support RAM > 3 GB. But that doesn't make it 64-bit.

Anyways your issue is sorted. Glad to know :-)

You can mark the thread Solved using **[COLOR="Red"]Thread Tools[/COLOR]** near the top of this page.

Happy Ubuntu-ing!

---


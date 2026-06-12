---
title: "eID Estonia - getting it to work"
date: 2010-03-13
forum: General Help
---

### Post by Steven_S on 2010-03-13
A question for Estonian Ubuntu users... 

I have installed Ubuntu as a dual-boot on my desktop, and am now trying to get everything to work (so that I can put Windows XP to sleep :-)). One of these things is using my Estonian eID to do Internet banking. 

There are instructions on this page - [http://ideelabor.ee/id-kaart/linux/](http://ideelabor.ee/id-kaart/linux/) - but it is all in Estonian. 

Would it be possible for someone who has done this before to walk me through what I have to do?

---

### Post by sdowney717 on 2010-03-13
google chrome browser has a translate extension. I ran it thru that site and it came back like this.

> UNIX yes ID card

Mida on vaja:

UNIXilaadset süsteemi, a piece on
a) distributions inside the OpenSC version numbers from 0.9.6 (not included) or
b) UNIXilaadsetsystem, which has the necessary resources to install the OpenSC algkoodist.
Supported cardreader.
Java software (this is necessary for the digital signature through the browser).
Saad Measure:

Use e-services for the project based on Mozilla browsers.
You digiallkirja DigiDoci portaalis ja U-netis
Sign and encrypt emails Thunderbird's e-mail client.
Participate in e-elections
What to do:

Install OpenSC. Depending on your system, either:
used for distribution or distributed install the necessary packages (for example, using Ubuntu,Debian, Fedora pakihaldurit) or
installeeri OpenSC algkoodist
Make sure that the card reader as well as OpenSC is properly installed andrunning.
Configure your browser to develop the EstonianID-card.
Make sure you have Java installed on your browser and itworks. Configure your browser to provide the digitalsignature.

---

### Post by Steven_S on 2010-03-14
Thanks! I tried that with Google-translate, and had installed: 

opensc (SmartCard utilities with support for PKCS#15 compatible cards)
Mozilla-opensc (Mozilla plugin for authentication using OpenSC)
libopensc2 (SmartCard library with support for PKCS#15 compatible smart cards)

Now I checked if the card reader was there following the instructions on this page ([https://ideelabor.ee/opensource/wiki/IdKaardiTarkvara/SuvalineUnix#Testimiseksjaprobleemidelokaliseerimiseks](https://ideelabor.ee/opensource/wiki/IdKaardiTarkvara/SuvalineUnix#Testimiseksjaprobleemidelokaliseerimiseks)) - apparently not: 

[URL="http://ideelabor.ee/id-kaart/linux/"]```
steven@steven-desktop:~$ opensc-tool --list-readers
Error: can't open /var/run/openct/status: No such file or directory
Error: can't open /var/run/openct/status: No such file or directory
Error: can't open /var/run/openct/status: No such file or directory
Error: can't open /var/run/openct/status: No such file or directory
Error: can't open /var/run/openct/status: No such file or directory
Error: can't open /var/run/openct/status: No such file or directory
Error: can't open /var/run/openct/status: No such file or directory
Error: can't open /var/run/openct/status: No such file or directory
Error: can't open /var/run/openct/status: No such file or directory
Error: can't open /var/run/openct/status: No such file or directory
Error: can't open /var/run/openct/status: No such file or directory
Error: can't open /var/run/openct/status: No such file or directory
Error: can't open /var/run/openct/status: No such file or directory
Error: can't open /var/run/openct/status: No such file or directory
Error: can't open /var/run/openct/status: No such file or directory
Error: can't open /var/run/openct/status: No such file or directory
[opensc-tool] reader-pcsc.c:1015:pcsc_detect_readers: returning with: No readers found
Readers known about:
Nr.    Driver     Name
0      openct     OpenCT reader (detached)
1      openct     OpenCT reader (detached)

```[/URL]
(hope I pasted that right)

So, my next issue is then: how to get the (USB connected) card reader to work? :-) It was plug-and-play in Windows, and it does have the normal red indicator light on, but...

Is there a way to see devices, as you would through the windows device manager?

*edit* Found out that I needed libccid. I'll try that first, and will get back...

---

### Post by sdowney717 on 2010-03-14
from terminal type in 
lsusb
to list devices on the usb bus
It looks like if you get the card reader working, it will work.

---

### Post by Steven_S on 2010-03-14
Here it is... 

Bus 005 Device 002: ID 076b:1021 OmniKey AG CardMan 1021

Still does not work though - it seems I need to do more to get this running. 

What I did sofar: 

Installed 
[INDENT]opensc (SmartCard utilities with support for PKCS#15 compatible cards)
Mozilla-opensc (Mozilla plugin for authentication using OpenSC)
libopensc2 (SmartCard library with support for PKCS#15 compatible smart cards)
[/INDENT] Got the card reader working (I suppose) 

Installed the certificates in Firefox. But then it gets fuzzy. 

I would think there would be Estonians around who are used to this sort of thing :-).

---

### Post by Steven_S on 2010-04-04
A follow-up question... I have received the instruction to download th eplugin for Firfox named "**[/usr/lib/onepin-opensc-pkcs11.so]("http://javascript%3Cb%3E%3C/b%3E:;")**" from this page: [https://ideelabor.ee/opensource/wiki/IdKaardiTarkvara/VeebisAutentimineMozillaga](https://ideelabor.ee/opensource/wiki/IdKaardiTarkvara/VeebisAutentimineMozillaga). 

When I click that link, nothing seems to happen. Any ideas?

Edit: I figured it out... The .so file appeared in the directory /Usr/lib/

Following instructions found online, in Firefox 3.5, I loaded the module manually: [LEFT]Edit->Preferences->Advanced->Encryption->Security Devices, then "load", locate the file opensc-pkcs11.so in /usr/lib and press ok. After that, everything seems to work. 

Still not sure what I did though :-).[/LEFT]

---


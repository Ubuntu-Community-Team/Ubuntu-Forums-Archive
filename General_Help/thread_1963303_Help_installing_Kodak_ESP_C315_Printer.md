---
title: "Help installing Kodak ESP C315 Printer?"
date: 2012-04-22
forum: General Help
---

### Post by pmanley on 2012-04-22
Help, I just bought a new printer, a Kodak ESP C315. I can't find any drivers for this printer. The automatic install process could not find this printer. How do I install it on Ubuntu Linux? I am using a cable from a USB port not a wireless connection. From what I can see on this forum and other web posts I may have bought the wrong printer. Thanks for any help or assistance offered. Peter. ](*,)

---

### Post by paulnewall on 2012-04-22
There is a driver here.
[http://sourceforge.net/projects/cupsdriverkodak/files/](http://sourceforge.net/projects/cupsdriverkodak/files/)
You should use the version c2esp24
download the file c2esp24.tar.gz
extract it
then read the file install to get detailed installation instructions.
 
Or, if you want to try a slightly more automated installation:
download c2espinstaller.sh
change it's properties to make it executeable
then execute it by opening a terminal and typing ./c2espinstaller.sh

---

### Post by pmanley on 2012-04-22
I doenloaded c2espinstaller.sh and ran it. In the dadabase there was only a C310 not the C315, but the C310 seems to work OK. Thanks very much for the help.:D

---

### Post by paulnewall on 2012-04-22
Do you know what the differences are between the C310 and the C315?

---

### Post by pmanley on 2012-04-23
No, I don't. Can you tell me? Will it make any difference to the operation of the printer? The C315 is working, but I have to say it seems very slow compared to my 15yr old HP printer.

---

### Post by paulnewall on 2012-04-24
I'm afraid that seeming slow is pretty normal for these printers and c2esp.
I'd expect some small difference in features between the C310 and C315, maybe it's just the size of the LCD display. I think that's bigger on the C315
If you can print using the C310 ppd file then it's working!

---

### Post by barnacle51 on 2012-08-26
It worked. I have a Kodak ESP 315 and have been trying for the last month to get it to run on Ubuntu 12.04. I installed 12.04.1 on a 16Gig USB stick. Went to printers and clicked on the "ADD PRINTER" and followed the directions. I used the ESP 310 driver. It worked the first time.

---


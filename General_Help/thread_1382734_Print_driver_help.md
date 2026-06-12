---
title: "Print driver help"
date: 2010-01-16
forum: General Help
---

### Post by thegreatpenguin on 2010-01-16
Hello I am unsure if this is the right section to post this but here it goes i have  a lexmark x2690 there is a deb package on lexmarks sight for my printer but being new to linux i am unsure how to manually install the driver I have read through a lot of documentation on installing packages but nothing has worked any help would be appreciated the driver i need to install is not listed under lexmark when you go to printer setup. The driver I need is located at [http://support.lexmark.com/index?page=content&id=DR860&actp=search&viewlocale=en_US&userlocale=EN_US&segment=DOWNLOAD&productCode=LEXMARK_X2690&searchid=1263657808991](http://support.lexmark.com/index?page=content&id=DR860&actp=search&viewlocale=en_US&userlocale=EN_US&segment=DOWNLOAD&productCode=LEXMARK_X2690&searchid=1263657808991)
PS i tried the generic cups driver but it does not do anything thank you.

---

### Post by patchwork on 2010-01-16
The package at the site you listed is an archived shell script.  Download the file using the links on the site, go to the location of the downloaded file (i.e. Places > Downloads  or where ever you downloaded the file to) click on the file.  This should open the archive manager.  Extract the enclosed script, and click it to run the script.

---

### Post by thegreatpenguin on 2010-01-16
Yea I figured it out but when I click on it to install it asks for a root password I put in the password and I get error wrong password but i use the same pass to open up synaptic so im kinda stuck not sure what to do.

---

### Post by patchwork on 2010-01-16
The same thing happens when I try it, but I am running 64 bit 9.10. Documentation states it works for 32 bit systems only.  Don't know if this could be the cause of the problems.

---

### Post by sisco311 on 2010-01-16
You have to run the script as root. Open a terminal (applications -> accessories -> terminal), and type 
```
sudo
```
type a space, drag and drop the script in the terminal window to get the full path to it. Press Enter and follow the instruction.

---

### Post by thegreatpenguin on 2010-01-16
Hey sisco thanks that did it my printer is working great.

---

### Post by RedRat on 2010-09-18
I know this is a late reply but I just installed the drivers from Lexmark for their Pro905 series printer combos. I merely had to extract the drivers from tar file and ended up with a *.sh file. I clicked on it and it asked for the password and away we went, slick and easy. I did this on my machine running 8.04 LTS. Prior to that I did have to install a small program (from Lexmark) that looked for a wireless network and it installed as a deb file, no problem. Must say I am impressed so far with Lexmark.

---

### Post by RedRat on 2010-09-20
Yesterday I ran the Lexmark script for installing the printer on my 8.04 machine but when I tried it with my 10.04 65 bit machine it did not work, I got an error message. Perhaps it has something to do with my 10.04 machine being 64 bit and my 8.04 being 32 bit.

Any suggestions?

Just talked to Lexmark, BTW got in quite quickly, and found that they do not support 10.04 64 bit at the present time. According to the support tech, they will probably be releasing a driver/support for it in the near future. Ho hum,,,,,,where have I heard that before? But who knows, maybe they will and we can see how fast they do respond to Linux users.

---


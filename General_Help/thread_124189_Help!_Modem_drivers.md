---
title: "Help! Modem drivers"
date: 2006-01-31
forum: General Help
---

### Post by Da Cosmonaut on 2006-01-31
Hi,

I have a lucent modem and I'm trying to install the drivers. Could you pleae tell me in which folder shall I put the ltmodem.ko and ltserial.ko files so the system recognizes my modem?

Thanks in advance

---

### Post by Da Cosmonaut on 2006-02-01
Please help, it is kind of urgent

tia

---

### Post by RAOF on 2006-02-01
Where did you get the drivers from?  Didn't the drivers come with a README file describing how to install them?

---

### Post by Da Cosmonaut on 2006-02-01
Not really, it was just a .tar.gz file that lead to another two .tar files named "control" and "data". In the last one come the two files I mentioned on the post. No Readme at all. The file is called "ltmodem-2.6.12-9-386_8.31b1_i386" and I got it from linmodems.technion.ac.il/packages/

---

### Post by ps2gimp on 2006-02-01
You really are better of building the driver from src as this ensures the driver matches the kernel you're running. Otherwise you'll to find a prebuilt driver package to match the kernel you've got.

Run to uname -r to check the driver package matches you're kernel.

Anyhows, copy the .ko's to "/lib/modules/2.6.12-9-386/other"
run "depmod -a"

edit (create) "/etc/modprobe.d/modem" and add the following

alias /dev/ttyLTM0 ltserial
alias char-major-62 ltserial
alias /dev/tts/LT0 ltserial

modprobe ltserial

and you're modem is device /dev/ttyLTM0

---

### Post by Da Cosmonaut on 2006-02-01
How can I build a driver from src??

---

### Post by Da Cosmonaut on 2006-02-02
Please, help!

---

### Post by RAOF on 2006-02-02
[QUOTE=Da Cosmonaut]How can I build a driver from src??[/QUOTE]
Well, you'd need to find the source code for the drivers.  It should be on the same site you got those binaries from.  In fact, it seems that the site ([linmodems.technion.ac.il/](linmodems.technion.ac.il/)) contains a step-by-step guide to installing winmodem drivers.

Incidentally, the .tar.gz you downloaded sounds like a slackware package - you might be able to convert that into something that can be automatically installed using alien.  To do that, you'd want to run:
```
sudo aptitude install alien
sudo alien -i ltmodem-2.6.12-9-386_8.31b1_i386
```
But that will require an internet connection, and *probably* won't work anyway.  Read the linmodems website ;).

---

### Post by RAOF on 2006-02-02
Or, even better, reading that website it seems that they have Ubuntu packages anyway.  This directory: [http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/Ubuntu/](http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/Ubuntu/) contains the packages, and a readme for building the drivers from source (which you shouldn't need, with the binary packages).  Work out what kernel you're runing - you can check that by running "uname -r" from a console.  Download the corresponding .deb from the linmodems website (it will probably be ltmodem-2.6.12-10-386_8.31b1_i386.deb).  You can then install this deb by running
```
sudo dpkg --install ltmodem-2.6.12-10-386_8.31b1_i386.deb
```

---


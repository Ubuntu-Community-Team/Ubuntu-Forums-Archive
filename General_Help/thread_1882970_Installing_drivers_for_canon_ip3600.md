---
title: "Installing drivers for canon ip3600"
date: 2011-11-18
forum: General Help
---

### Post by Brian R. on 2011-11-18
Now running 11.10 and originally had my networked ip3600 printing on earlier versions of ubuntu, and it kept working on all my updates. I could even get it to work with the ip4600 drivers. But after having to reinstall 11.10 I can no longer get it to work. I have tried all the ideas i have seen on the forums so far, including the codes to modify the drivers from canon for libcupsys2/libcups2, but still no joy, only end up with broken packages, that I have to repair, and it will not run as it cannot find usr/lib/cups/filter/pstocanonij, "please install it"
where do I get that file and how do I install it?

thanks

---

### Post by Brian R. on 2011-11-20
Go to the following site [http://askubuntu.com/questions/75014/how-can-i-install-a-canon-driver](http://askubuntu.com/questions/75014/how-can-i-install-a-canon-driver) and do the first answer "I found the solution".
But you also need the canonip3600.ppd file which can be extracted from the  file from this site [http://software.canon-europe.com/sof...336.asp?model=](http://software.canon-europe.com/sof...336.asp?model=).
extract all the files and it will be in the usr folder of the extracted files.

---

### Post by Yvee on 2012-04-21
Suppress the ip3600 printer from your system.

Switch off the printer

Type in a terminal window:

sudo add-apt-repository ppa:michael-gruz/canon
sudo apt-get update
sudo apt-get install cnijfilter-common cnijfilter-ip3600series

then switch on the printer. Normally it works and you can print out the test page.

---


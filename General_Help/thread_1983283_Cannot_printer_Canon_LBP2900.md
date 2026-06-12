---
title: "Cannot printer Canon LBP2900"
date: 2012-05-20
forum: General Help
---

### Post by ohlalavina on 2012-05-20
On Ubuntu 11.10 I use this printer not problem, but reinstall Ubuntu 12.04LTS, I not print

[https://help.ubuntu.com/community/CanonCaptDrv190](https://help.ubuntu.com/community/CanonCaptDrv190)

Help me! Pl Thank

---

### Post by shankara on 2012-05-20
It worked for me, but, need to load the driver module every time after reboot. 
It worked for me with CAPT versions 2.20 and 2.40. 
I used a shell script downloaded from a website and replaced the drivers with newer versions(2.40). That script can be downloaded from the link which is pasted in the question. 

The script can be downloaded from this link.

[http://radu.cotescu.com/how-to-install-canon-lbp-printers-in-ubuntu/](http://radu.cotescu.com/how-to-install-canon-lbp-printers-in-ubuntu/)

But, need to execute following commands after every reboot.

sudo modprobe usblp
ls -l /dev/usb/lp0
sudo /etc/init.d/ccpd restart

---


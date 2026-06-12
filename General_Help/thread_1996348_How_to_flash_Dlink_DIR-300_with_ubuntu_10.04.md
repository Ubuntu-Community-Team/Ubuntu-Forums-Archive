---
title: "How to flash Dlink DIR-300 with ubuntu 10.04"
date: 2012-06-04
forum: General Help
---

### Post by fatboy07 on 2012-06-04
Hello Guys, I want to flash my DLINK DIR-300 with DD WRT build 14311 using a laptop with UBUNTU 10.04. hope somebody can help me.. thanks in advance.

---

### Post by dino99 on 2012-06-04
follow the dlink wiki

[http://translate.google.com/translate?hl=fr&ie=UTF8&prev=_t&sl=auto&tl=en&u=http://www.dlink.ru/ru/products/5/1270.html](http://translate.google.com/translate?hl=fr&ie=UTF8&prev=_t&sl=auto&tl=en&u=http://www.dlink.ru/ru/products/5/1270.html)

Question: How to fill a new firmware to the switch or other control devices?
A:

To print / web servers, this can be done from PSAdmin / ISAdmin clicking on the option "Firmware Update" and then follow the instructions.

Most switches require replacement when the two flashing firmware: PROM and RUNTIME. First, you need to flash the PROM code, then RUNTIME.

Report this sequence will lead to the output of the switch down (repair under warranty can not be)!

For the firmware must be connected to the switch through the console port or the network. It also requires TFTF-server (for example, comes with D-View).

Runs on the Host TFTP-server, the switch through the console option is allowed to update the software and should contain the complete path to the firmware binary files. Next, the switch resets and updates the software.

---

### Post by colin.p on 2012-06-04
> **fatboy07 said:**
> Hello Guys, I want to flash my DLINK DIR-300 with DD WRT build 14311 using a laptop with UBUNTU 10.04. hope somebody can help me.. thanks in advance.

The flashing of your router has nothing to do with what OS you are using.
Go to the appropriate DD WRT wiki article for your router and follow the instructions. The problem may arise with the browser you use. I used Firefox to put DDWRT on my Dlink 601 and it updated fine. I don't know about Chrome, but if it doesn't work, just try Firefox.

seems that the dir 300 uses the same instructions as the 600:[http://www.dd-wrt.com/wiki/index.php/D-Link_DIR-600_/_300vB](http://www.dd-wrt.com/wiki/index.php/D-Link_DIR-600_/_300vB) However this for revision B.
For the old revision A it is:[http://www.dd-wrt.com/wiki/index.php/D-Link_DIR300_rev_A](http://www.dd-wrt.com/wiki/index.php/D-Link_DIR300_rev_A)

You will have to figure out which revision of router you have.

WOW after looking at the instructions on the revision A router, I'd say screw it and go for the newer routers. I paid $20 for my 601.

---

### Post by fatboy07 on 2012-06-06
Thanks for the reply, I will try to flash my router. my router rev is A1. thansk you again and update what happen. :)

---

### Post by pbrane on 2012-06-06
Chrome works fine for flashing DD-WRT images.

---

### Post by fatboy07 on 2012-06-06
so dumb, dont know where to start, can somebody send me a screen shot to do this flashing using ubuntu 10.04? :)

---

### Post by Kr0nZ on 2012-06-06
I used the steps located at [http://wiki.openwrt.org/toh/d-link/dir-300]("http://wiki.openwrt.org/toh/d-link/dir-300"), to flash my dir-300 with openwrt a few weeks ago.
But only rev A1 and B1 are supported, mine was a D1 and it didnt work (not enough flash mem)

[http://www.dd-wrt.com/wiki/index.php/D-Link_DIR-300_rev_A]("http://www.dd-wrt.com/wiki/index.php/D-Link_DIR-300_rev_A") has the steps for ddwrt

EDIT:
To initially flash youll need a tftp server and the firmware files on your ubuntu machine

You can install a tftp server by typing
```
sudo aptitude install tftpd-hpa
```

then you can put your firmware files in '/var/lib/tftpboot' (read the openwrt link, it will become clear why)

What firmware files you need is up to you though. You should check the ddwrt forum.

---

### Post by fatboy07 on 2012-06-09
by the way, can I do this with a laptop? or I need a desktop machine?

---


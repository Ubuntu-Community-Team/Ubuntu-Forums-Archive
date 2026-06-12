---
title: "A little help please?!"
date: 2006-04-15
forum: General Help
---

### Post by morbid_bean on 2006-04-15
I am trying to set up my moden via usb port  in ubuntu, im using the guide from [http://docs.linux.com/article.pl?sid=03/05/14/123256&tid=20&tid=14](http://docs.linux.com/article.pl?sid=03/05/14/123256&tid=20&tid=14) . ok now here is the problem when i type "insmod usbserial vendor=0x0870 product=0x0001" I get   "insmod: can't read 'usbserial': No such file or directory" So that means i gotta make it *i think*  so then i type "mknod /devttyusb0 c 188 0" and i then get "mknod: `/devttyusb0': Permission denied" now what the heck? please someone help me!!!??

---

### Post by PriceChild on 2006-04-15
What model is your modem? Could be handy to know whether it's dialup, adsl, dsl, cable etc.

P.s. what's the point making two topics about this when the first is still on the frontpage.

---

### Post by morbid_bean on 2006-04-15
the modem is an external metricom wireless modem. company name is ricochet model no. is 21100

---

### Post by morbid_bean on 2006-04-15
its dial up

---


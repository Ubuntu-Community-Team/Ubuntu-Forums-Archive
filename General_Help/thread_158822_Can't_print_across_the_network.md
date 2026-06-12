---
title: "Can't print across the network"
date: 2006-04-11
forum: General Help
---

### Post by ham_n_bill on 2006-04-11
I know it's something simple. The printer has worked with Mepis and Suse, i just 
can't print to it from Ubuntu. I have tried multiple combinations in the cups printer
url and the hp deskjet direct. and get nowhere

HP Photosmart on a 10/100 lan with a static Ip of 192.168.1.107 for the Hawking
USB print server...Anyone with any suggestions????   ](*,)

---

### Post by Chuck_W on 2006-04-11
My setup is similar. The printer is a Kyocera Mita FS-1010 and I also use a Hawking Tech usb print server. I was never able to get CUPS working. Ended up using unix (LPD). The ip is static and the queue is lp1. The queue is important. Nothing will print if you leave it out. So far this works well for me although I haven't tried any fancy stuff. One thing I found is that if a particular setup doesn't work it is better to delete that printer and start over. Changing the settings doesn't seem to take otherwise.

---

### Post by ham_n_bill on 2006-04-21
Thanks for your help. I never did get it to work. Finally installed Kubuntu.. Good Old KDE
found it without a problem............

---


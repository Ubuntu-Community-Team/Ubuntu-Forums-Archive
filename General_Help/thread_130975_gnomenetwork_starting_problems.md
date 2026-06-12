---
title: "gnome/network starting problems"
date: 2006-02-15
forum: General Help
---

### Post by mac_9863859 on 2006-02-15
hi all together (sorry for my english ;-) )

I am only able to log in to gdm if I disable mit networkdevice (ifdown -a). After log in into gdm it is possble to switch on the networkinterface. If I try to log in with eth0 still runnig I get an brown backround and nothing happen...

OK this is one problem and I have some more ;-)
I try to use nfs-kernel-server.... the nfsd cant start during the bootprocess. Ich have to do the whole step I´ve written above. Once in gdm I have to switch on the eth0 with the "network-admin". After restart the nfsd it works fine. BUT if I start the eth0 (inside gdm) with an shell (with ifup -a or ifconfig eth0 up.....) the nfsd can´t start !!!

So do anybody know the difference between pressing the aktivation-button at the "network-admin" and the shell-comands to start the networkdevice ??

Thanks a lot

greating mac

---


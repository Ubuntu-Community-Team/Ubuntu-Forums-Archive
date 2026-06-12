---
title: "usb adsl modem pain please help"
date: 2006-04-09
forum: General Help
---

### Post by krizalit on 2006-04-09
hi,
i use ubuntu 5.10 and i have a d-link dsl210 usb adsl modem. when i first time install ubuntu there was no internet conection so i didnt learn anything and have too much problems.
second intallation with my friends adsl modem (connecting to modem with ethernet) is easy. by installation ubuntu take something from internet and it works fine. after installation i do apt-get upgrade and i installed pppoe from internet.

but my problem is i cant use ubuntu with my usb adsl modem. when i look through device manager i see that ubuntu has dedected my adsl modem as "connexant adsl modem" in usb port 
i do lsusb and i see it again. but when i do pppoconf it can see only eth0 
so how can i show my modem to ubuntu and let use usb modem to connect internet ?
is there something i dont know to give some parameters for pppoe ?

---

### Post by kagashe on 2006-04-12
After connecting the modem to USB port click on System>Administration>Networking and check whether you can see another Ethernet interphase eth1. If yes configure it further as per the modem document (and not as per pppoe).

If you don't see eth1 then check in /var/log/messages file. I am writing what messages I got for my USB ADSL modem:
>  usb 2-2: new full speed USB device using uhci_hcd and address 2
usb 2-2: configuration #2 chosen from 2 choices
Keeping default configuration with /sys//devices/pci0000:00/0000:00:0b.1/usb2/2-2
eth1: register usbnet at usb-0000:00:0b.1-2, CDC Ethernet Device, 00:08:5c:5d:97:59
usbcore: registered new driver usbnet
usbnet: loaded successfully

kagashe

---

### Post by djgenesis on 2006-04-12
I am facing the same problem. 
I can't see the ADSL modem in the nework-admin feature.
Here is my system response, am i doing something wrong?
```
Apr 12 19:54:09 localhost kernel: usb 1-2: USB disconnect, address 3
Apr 12 19:54:34 localhost kernel: usb 1-2: new full speed USB device using uhci_hcd and address 4
Apr 12 19:54:35 localhost usb.agent[9722]:      speedtch: already loaded
Apr 12 19:54:35 localhost usb.agent[9722]:      speedtouch: loaded successfully
Apr 12 19:54:35 localhost kernel: usb 1-2: khubd timed out on ep0in
Apr 12 19:54:35 localhost usb.agent[9790]:      speedtch: already loaded
Apr 12 19:54:35 localhost usb.agent[9790]:      speedtouch: loaded successfully
Apr 12 19:54:36 localhost usb.agent[9785]:      speedtch: already loaded
Apr 12 19:54:36 localhost usb.agent[9785]:      speedtouch: loaded successfully

```

---


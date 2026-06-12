---
title: "HP Photosmart Premium c310 printer"
date: 2012-06-26
forum: General Help
---

### Post by Quarkrad on 2012-06-26
I have two PCs both running 12.04, the only difference, that I cannot see is relevant, is one is 32bit(has problem) and the other 64bit(works).  Both machines have the latest hp driver, hplip 3.12.6, for my Photosmart Premium printer (c310).  The 32bit machine is usb connected and can print but not scan, the 64bit machine is wirelessly connected and can print and scan. I've deleted the hp driver off the 32bit machine and re-installed - it still will not scan.  I removed the usb connection and connected it wirelessly - it still will not scan!  Comes up with the same error message:

[[IMG]http://t.imgbox.com/aaiHMK8a.jpg[/IMG]](http://imgbox.com/aaiHMK8a) 

when the printer was usb connected the error message was the same but after the 'hpaio:/net/  I think there was a ref to usb.

Something on this machine will not let me scan!  I install Scanlite from the software centre (I normally use xsane) and it just says Sorry, Opening the selected scanner failed.  Any advice on my next move?

---

### Post by dino99 on 2012-06-26
are you sure about 192.168.1.2 address ? or do you have some firewall rule conflicting ?

sudo update-usbids && sudo update-pciids

sudo dpkg-reconfigure -phigh -a
(can take a while, be patient)

---

### Post by Quarkrad on 2012-06-26
Thanks - no change.  This is the output of your command:

liz@lizubuntu:~$ sudo update-usbids && sudo update-pciids
[sudo] password for liz: 
--2012-06-26 17:41:04--  [http://www.linux-usb.org/usb.ids](http://www.linux-usb.org/usb.ids)
Resolving [www.linux-usb.org](www.linux-usb.org) ([www.linux-usb.org](www.linux-usb.org))... 216.34.181.97
Connecting to [www.linux-usb.org](www.linux-usb.org) ([www.linux-usb.org)|216.34.181.97|:80](www.linux-usb.org)|216.34.181.97|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 478065 (467K) [text/plain]
Saving to: `/var/lib/usbutils/usb.ids.new'

100%[======================================>] 478,065      146K/s   in 3.2s    

2012-06-26 17:41:07 (146 KB/s) - `/var/lib/usbutils/usb.ids.new' saved [478065/478065]

Done.
Downloaded daily snapshot dated 2012-06-25 14:42:27

I put the USB cable/connection back and rebooted.  Still no scan - get this error message:

See attached

---

### Post by Quarkrad on 2012-06-26
Oops - I had 3.12.4 on my 64 bit machine, not 3.12.6.  Reinstalled 3.12.4 on 32 bit machine and all is well.  Looks like a problem with .6

---


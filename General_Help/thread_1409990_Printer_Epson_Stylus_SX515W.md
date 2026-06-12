---
title: "Printer Epson Stylus SX515W"
date: 2010-02-18
forum: General Help
---

### Post by fbjoey on 2010-02-18
Anyone know if it will work on ubuntu?

---

### Post by ellgor on 2010-02-18
Hi,

I have the Sx115 all in one, it works fine in 9.10, you do need to get the drivers from the "Avasys" site, its for Epson's, I can recommend the Imagescan app they have as well.

Regards, Ellgor.

---

### Post by mil2house on 2010-05-26
> **ellgor said:**
> Hi,

I have the Sx115 all in one, it works fine in 9.10, you do need to get the drivers from the "Avasys" site, its for Epson's, I can recommend the Imagescan app they have as well.

Regards, Ellgor.

Hallo.

Know You, if work fine in Ubuntu 10.04? All parts printing and scanning?

Thanks very much! 

PS: Sorry for my english. :popcorn:

---

### Post by gabitogol on 2010-07-14
System:

Ubuntu 9.10 x86_64 bits
kernel 2.6.28-18-generic


I downloaded 
[http://avasys.jp/eng/linux_driver/download/lsb/epson-inkjet/escpr/](http://avasys.jp/eng/linux_driver/download/lsb/epson-inkjet/escpr/)

And install the printer

[http://avasys.jp/eng/linux_driver/download/lsb/epson-inkjet/escpr/README.html](http://avasys.jp/eng/linux_driver/download/lsb/epson-inkjet/escpr/README.html)

I can print by usb or wifi but I can´t scan yet.

Any ideas?

---

### Post by ellgor on 2010-07-14
Hi,

Go to the "Avasys" site and get their Imagescan package, go through the form filling in bit (for your model) and when you get to the download page scroll right down until you see "Iscan or Imagescan deb" which is a completely seperate app  from the full printing package, once downloaded use gdebi to automatically install it, needs a reboot to work properly.  

Regards, Ellgor.

---

### Post by gabitogol on 2010-07-14
It work like charm, thanks a lot Ellgor!

In my case I used:

[http://linux.avasys.jp/drivers/iscan-data/1.0.1/iscan-data_1.0.1-1_all.deb](http://linux.avasys.jp/drivers/iscan-data/1.0.1/iscan-data_1.0.1-1_all.deb)
[http://linux.avasys.jp/drivers/iscan/2.25.0/iscan_2.25.0-1.ltdl7_amd64.deb](http://linux.avasys.jp/drivers/iscan/2.25.0/iscan_2.25.0-1.ltdl7_amd64.deb)
[http://linux.avasys.jp/drivers/scanner-plugins/iscan-network-nt/1.1.0/iscan-network-nt_1.1.0-2_amd64.deb](http://linux.avasys.jp/drivers/scanner-plugins/iscan-network-nt/1.1.0/iscan-network-nt_1.1.0-2_amd64.deb)

---

### Post by batfink10 on 2010-07-14
It works fine for me under 10.04 - all via wi-fi too, no cables.

Printer = no Avasys driver required, it just worked (wi-fi enabled)
Scanner = Imagescan software required from Avasys, but after that, it worked fine.

---

### Post by tpp on 2010-08-06
I just bought this printer/scanner and got it working Ubuntu 10.04 amd64 following the advice in this thread. I got everything working using wi-fi 

1) Connected the printer to my wireless network by using the menus on the device

2) Downloaded and installed the avasys driver

[http://linux.avasys.jp/drivers/lsb/epson-inkjet/stable/debian/dists/lsb3.2/main/binary-amd64/epson-inkjet-printer-stylus-tx550w-series_1.0.0-1lsb3.2_amd64.deb]("http://linux.avasys.jp/drivers/lsb/epson-inkjet/stable/debian/dists/lsb3.2/main/binary-amd64/epson-inkjet-printer-stylus-tx550w-series_1.0.0-1lsb3.2_amd64.deb")

3) Added new printer (System->Admin->Printers) with the LPD protocol and pointed it at:

ldp://192.168.1.90

Where [192.168.1.90 is the IP address of the printer - it tells you on the device menus] And that was the printer up and running!

4) To get the scanner working I simply installed the 3 imagescan packages linked by gabitogol and then edited the file:

sudo gedit /etc/sane.d/epkowa.conf

and at the bottom inserted the lines:

net 192.168.1.90

and restarted and boom the scanner works! Thanks all for the help.

---


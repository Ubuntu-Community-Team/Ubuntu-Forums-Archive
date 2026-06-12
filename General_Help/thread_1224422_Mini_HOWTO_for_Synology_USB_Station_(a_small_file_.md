---
title: "Mini HOWTO for Synology USB Station (a small file &amp; printer server)"
date: 2009-07-27
forum: General Help
---

### Post by Macchi on 2009-07-27
The Synology USB Station works in Ubuntu for file sharing and printing without any modifications to the system.(despite the statements from the supplier that it is not compatible with Linux!)

FILE SHARE
To access the file shares got to Places->Network and browse to desired file share (admin, private, or public). The usernames for admin is apparently just "admin" and for private is "guest". You may also access the ftp area through Places->Connect to Server->FTP (with login) 

PRINTER
Set up your printer as usual in System->Administration->Printing->New Printer and choose "Internet Printing Protocol" from the list. Provide the IP address for the USB Station and the queue should be /printers/usbprinter1 or /printers/usbprinter2 



CONCLUSIONS 
On the plus side the Synology USB Station has a small footprint and low price tag. It can replace a small server for printing and file sharing, offering silent operation and low power consumption.
I love the concept of simple products but unfortunately I cannot recommend the Synology USB Station without many reservations and warnings. 
At first users will discover that smb and ftp file shares have a weird storage layout, since it is not possible to access by ftp the files stored through smb and vice versa. Thus files cannot be shared through different access protocols! 
Support is weak or not available since very few answers are nor maintenance of the product, and the two latest firmware releases are from mid 2006 and 2007. 
Due to the lack of updates we may expect lower reliability, limited functionality and eventually many bugs. This particular unit that I have been testing has to be restarted regularly since it somewhat loses contact with the USB disk.
Furthermore no Linux support is mentioned despite the fact that many of their products are probably based on Linux and on other open source software. They use code licensed under GPL but make the source code available only upon specific request. This may be a violation of the licence that is clear to assure the availability of the source code. 
(Please correct me if I am wrong, maybe I have only bad luck with a defective unit, but I am sure the problem must be related more to software than to hardware.

---

### Post by t4thfavor on 2009-07-27
Check and see if Openwrt or openslug (I think thats what its called) will run on it. The openslug is for the linksys nslu2 which is the same type of device. They have hacked it into a secure, and open source NAS device with printer support, and a whole lot of other devices, including wireless USB devices to make it a wireless USB file/print server. Perhaps the Synology device has the same heritage as the nslu2.


If its a Synology DS101 check here [http://www.nslu2-linux.org/](http://www.nslu2-linux.org/) or just go there anyways and see if its supported.

---

### Post by Macchi on 2009-07-27
Thanks t4thfavor but I have not yet found any references on successful opennwrt or openslug etc on the Synology USB Station. Most probably due to its proprietary design and limited hardware, hawing only 16MB RAM and 4MB flash.  

> **t4thfavor said:**
> Check and see if Openwrt or openslug (I think thats what its called) will run on it. The openslug is for the linksys nslu2 which is the same type of device. They have hacked it into a secure, and open source NAS device with printer support, and a whole lot of other devices, including wireless USB devices to make it a wireless USB file/print server. Perhaps the Synology device has the same heritage as the nslu2.


If its a Synology DS101 check here [http://www.nslu2-linux.org/](http://www.nslu2-linux.org/) or just go there anyways and see if its supported.

---

### Post by Macchi on 2009-08-17
After a couple of weeks of new tests with the Synology USB Station, I am sorry to say that it performs well below our expectations. 
The device has to be restarted a few times per week, printing seems to work OK but file sharing is very unreliable! 
I will attempt to contact Synology once more, fearing that there will be no further technical support for that product. 

PS: I will replace the USB station back again by a quiet old desktop Pentium III 500MHz 256MB running Ubuntu and configured as file and printer server.

---


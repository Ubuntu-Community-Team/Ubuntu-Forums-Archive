---
title: "Need help getting printer working on network"
date: 2009-10-22
forum: General Help
---

### Post by Rick Abraham on 2009-10-22
Hi guys I have just bought a Brother HL-2140 laser printer, I firstly downloaded the linux drivers I needed from Brothers website.

brhl2140lpr-2.0.2-1.i386.deb
cupswrapperHL2140-2.0.2-1.i386.deb

I installed the drivers and the printer works fine when it's plugged into a USB port.
But I want to put the printer on my network so it can be used by other pc's aswell.
I bought a D-Link DPR-1020 print server which is Linux compatiable.
I plugged my printer into the print server and plugged the print server into my router.
The DHCP server has issued the print server with a IP address of 192.168.0.100

What do I do now to get the printer working on the network with Ubuntu 9.04.
I went to System > Administration > Printing and I selected the properties of my printer 
I have read that I need to change the URL address at the moment it is 

usb://Brother/HL-2140%20series

What do I change it to and is there anything else I need to do ?

---

### Post by P4man on 2009-10-22
remove that printer again, it refers to the local printer which is no longer there.

Instead, add a new network printer. Cant say how to configure it exactly as it depends on the printserver, but there is good chance it will be detected automatically

---

### Post by akakingess on 2009-10-22
also, couldn't it just have stayed attached to the Ubuntu machine and Cups would have allowed it to be shared across even a Windows network?

---

### Post by P4man on 2009-10-22
> **akakingess said:**
> also, couldn't it just have stayed attached to the Ubuntu machine and Cups would have allowed it to be shared across even a Windows network?

Yeah but that requires the host to be powered on all the time. A small printserver like that is quite convenient.

---

### Post by Rick Abraham on 2009-10-23
Thanks guys I figured it out.
I deleted the local printer as you said and created a new network printer.
Put the print servers IP address in where it asked me for a HOST location and it started to work.
Cheers

---

### Post by espresso_steve on 2009-10-23
Thanks people. Got my network printing sorted with this info.

---


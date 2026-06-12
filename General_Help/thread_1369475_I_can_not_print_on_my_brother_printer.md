---
title: "I can not print on my brother printer"
date: 2010-01-01
forum: General Help
---

### Post by jcampbell12 on 2010-01-01
Hi there,

I am running ubuntu 9.04 and am having trouble printing. My Brother DCP 330c printer is detected however I have to manually chose a printer driver all of which do not work with the printer. I have tried downloading a printer driver from the brother website and tried to install it. But the driver does not work apparently because I am not a super user

can anyone help

cheers

josh :sad:

---

### Post by Pollox on 2010-01-01
I take it you followed the directions at [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html"), and successfully found the .deb file for the cups driver?  Perhaps you issued some of their console commands without typing "sudo" before each of them (or type "sudo su" at the beginning, and forego the "sudo" stuff?  You could probably just double-click the .deb file, enter your password, and click install.

---

### Post by plucky on 2010-01-01
> **jcampbell12 said:**
> Hi there,

I am running ubuntu 9.04 and am having trouble printing. My Brother DCP 330c printer is detected however I have to manually chose a printer driver all of which do not work with the printer. I have tried downloading a printer driver from the brother website and tried to install it. But the driver does not work apparently because I am not a super user

can anyone help

cheers

josh :sad:

The driver should be packaged in synaptic package manager.

Search for DCP-330C and it should find the **brother-cups-wrapper-bh7** and **brother-lpr-drivers-bh7** 
Install both.Then connect and power on your printer and go to **System > Administration > Printing** add a new printer.It should then find the printer and install it.

You might have to select the correct driver which should now be in the list.

Good Luck

---


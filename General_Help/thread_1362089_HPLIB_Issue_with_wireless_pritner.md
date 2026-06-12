---
title: "HPLIB Issue with wireless pritner"
date: 2009-12-22
forum: General Help
---

### Post by Image0fman on 2009-12-22
Printer = Officejet 6480
I installed the latest hplib and went through the hp-setup. I get the printer to work no problem with a direct connection via usb. When I try to install it as a wireless connection hp setup states it doesn't detect any wireless printers but my J6480 is wireless capable! Any idea what the problem may be? Thanks in advance

---

### Post by synapsys on 2009-12-22
Is your computer wireless capable?

If it is, is your wireless card set up properly?

---

### Post by Image0fman on 2009-12-22
No it's hard-lined to the router, shouldn't it be able to detect a wireless printer?

---

### Post by synapsys on 2009-12-22
> **Image0fman said:**
> No it's hard-lined to the router, shouldn't it be able to detect a wireless printer?

Assuming you have a wireless router, yes.

First thing I would do is log into the router config page and make sure the printer is connecting to the router, and go from there.

---

### Post by lavinog on 2009-12-23
Does the printer have a screen to configure it with...if so give it a static ip address.

---

### Post by steveneddy on 2009-12-23
> **synapsys said:**
> Assuming you have a wireless router, yes.

First thing I would do is log into the router config page and make sure the printer is connecting to the router, and go from there.

The router must be a wireless router and you will need to configure your printer to connect wirelessly.

This is probably in the manual.

If the laptop is wireless and the printer is wireless they will have to both be able to connect to the wireless router, they will not see each other wirelessly.

---

### Post by lavinog on 2009-12-23
I just noticed the screenshot says to connect the wireless device via usb to set it up wirelessly.

---

### Post by Image0fman on 2009-12-23
Thanks for the replies. This printer is already on the network and serves 6 clients _wirelessly_. It also has a static ip address. It works on linux when its connected via usb. When I go through hp-setup to try and configure it to setup a wireless printer it doesn't detect my J6480 and I get the screen I posted. My hplib is up to date and I installed form hp's opensource site as well as installing from the terminal. I'm stumped. Any other suggestions?? I really appreciate yall help thx

---

### Post by lavinog on 2009-12-23
What does the wireless detection page say when the printer is connected using the usb? (the screenshot says to connect with usb and click refresh...what happens when you do this?)

---

### Post by Image0fman on 2009-12-23
It shows exactly what you see in the screenshot

---

### Post by lavinog on 2009-12-23
You might not need to do this step if the device is already setup with an ip address.  I haven't setup a network printer in a while, but redo the setup but select network printer instead, and give it the ip address of the printer.

I think the step you are trying to accomplish is mainly for setting the device up to work with the access point.

---

### Post by Image0fman on 2009-12-23
Hey lavinog 

WOW. Worked like a charm, just had to assign the ip in the adanced tab for network printers location.. Thanks very much

---


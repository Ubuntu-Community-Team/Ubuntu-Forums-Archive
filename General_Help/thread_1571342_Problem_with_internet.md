---
title: "Problem with internet"
date: 2010-09-09
forum: General Help
---

### Post by dhanvsagar on 2010-09-09
Hi
I am using dell inspiron n1410 laptop.
I am absolutely new in linux.
I am from india & using BSNL broadbad internet.
Now, i am not able to  use internet in ubandu. I dont know how to configure that.
while entering 'ifconfig' in the tenminal, a message like no device/hardware found appears.
Pls heelp me

---

### Post by 3Miro on 2010-09-09
You probably need a proprietary driver for the WiFi on your Laptop. The best way to resolve this is:

1. Find a wired connection and plug it in. Ubuntu should automatically connect.

2. Go to System -> Admin -> Software Updates, check for new updates and update your system.

3. After rebooting, go to System -> Admin -> Hardware Drivers and select the proprietary driver listed there.

Technically you can go to step 3 without installing all the updates from step 2 (just make sure to reload the software database by choosing "check for updates"), however, the above is a safer way and you have to update anyway.

---

### Post by dhanvsagar on 2010-09-09
Sorry
I connected the cable wire but ubuntu is not detecting any connection. dats my problem

---

### Post by fragos on 2010-09-09
I've an 1420n in the USA. The "n" in that model name means that this laptop shipped with Ubuntu and came with the Intel WiFi chip set that's automatically recognized and configured for Ubuntu. To determine which WiFi chip set in in yours, open a terminal window and run "lspci |grep Network" which will tell you which chip set WiFi is using. If it's Intel you should have been OK. The other chip set choice is Broadcom which will require some work to get running. Search this forum for chip set number you got with lspci and you'll find directions. It's been a few years since I got a Broadcom WiFi working so you'll want newer instructions than I used back then.

---


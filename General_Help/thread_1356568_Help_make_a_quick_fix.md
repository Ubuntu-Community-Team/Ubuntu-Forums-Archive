---
title: "Help make a quick fix"
date: 2009-12-16
forum: General Help
---

### Post by swat-leader on 2009-12-16
Hi all,
        I have a Huwaie K3520 USB mode. Now in the new 9.10 this is not reconised as a USB modem so to use it i have to unmount the virtual CD-R and the SD card reader and then go into temainal and type all this code every time i whant to use it..

is there a way to make a script so i dont have write tthis each time??? i have included the coding so someone can help me do this.. I have also reported it as a bug and is still getting looked into.

(code typed in terminal)

sudo rmmod usb-storage

sudo modprobe -r option

sudo modprobe -r usbserial

sudo modprobe usbserial vendor=0x12d1 product=0x1001

sudo pppd ttyUSB0

Thanks 

Shane

---

### Post by philinux on 2009-12-16
Ok.

---

### Post by swat-leader on 2009-12-16
thanks for that make life that little bit easier for me and others

---

### Post by b3rylord on 2010-11-05
Hi, I am having similar promblems getting a K3520 dongle to work with Ubuntu 10.10 and also thought I had it solved by running the following
sudo rmmod usb-storage

sudo modprobe -r option

sudo modprobe -r usbserial

sudo modprobe usbserial vendor=0x12d1 product=0x1001

sudo pppd ttyUSB0

unfortunately the provider did not specify that it had to be run EACH time I plugged in the dongle....or have I misunderstood???
 
I foolishly bought "Linux the complete manual" ISBN 1-906372-69-1 which glibly states that Ubuntu will recognise the dongle and would bring up network manager, well it did not....I still cannot find the network manager!!!!  lol, where am I goung wrong? There seem to be many ways of doing the same thing in Linux and I cannot seem to get a clear overview of the difference between these different ways....can anyone point me towards such a guide..?

---


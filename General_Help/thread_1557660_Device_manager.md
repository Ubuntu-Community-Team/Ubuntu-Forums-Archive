---
title: "Device manager"
date: 2010-08-21
forum: General Help
---

### Post by Bphillips on 2010-08-21
Im new to Ubuntu been using windows, is there like a device manager in Ubuntu 10.04LTS..where i can add or remove hardware.

---

### Post by ngrieb on 2010-08-21
I'm not quite sure about this but you can try a:

sudo lshw >> hardwarelist.txt

to see if the hardware is showing up and or being used. It should create a text file in your current directory with all of the current hw listed. If you don't see it there post back.

---

### Post by Bphillips on 2010-08-21
> **ngrieb said:**
> I'm not quite sure about this but you can try a:

sudo lshw >> hardwarelist.txt

to see if the hardware is showing up and or being used. It should create a text file in your current directory with all of the current hw listed. If you don't see it there post back.


I dont know where to go to type sudo lshw >> hardwarelist.txt  in at.

---

### Post by philinux on 2010-08-21
> **Bphillips said:**
> Im new to Ubuntu been using windows, is there like a device manager in Ubuntu 10.04LTS..where i can add or remove hardware.

What's the problem?

---

### Post by Bphillips on 2010-08-21
> **philinux said:**
> What's the problem?

I'm having hardware problems and was wondering where to find out whats being detected or not detected.

---

### Post by Ginsu543 on 2010-08-22
> **Bphillips said:**
> I dont know where to go to type sudo lshw >> hardwarelist.txt  in at.
To run this command and to run other commands which can give you information about your hardware, you need to open Terminal (Accessories --> Terminal), which is the Linux Command Line Interface. If you run the above command, you will tell Ubuntu to run the program lshw with root privileges (Linux requires you to have root privileges to access sensitive information such as hardware info). Lshw (which short for [l]i[s]t [h]ard[w]are) will look through your system and list pertinent information about it. The >> hardwarelist.txt part of the command tells lshw to take it output and save as a text file called "hardwarelist.txt." You can then open the text file to see the output.

Another helpful command is lspci (which lists all the hardware connected to the pci bus) and lsusb (which lists all the hardware connected through the usb bus).

---


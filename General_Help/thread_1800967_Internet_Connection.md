---
title: "Internet Connection"
date: 2011-07-09
forum: General Help
---

### Post by niko001 on 2011-07-09
I installed the latest Ubuntu on my ACER AspireONE as I had some issues with Windows. Installation done with no problem but I have no internet connection. As I am new to UBUNTU I do not know how to configure the intenet connection.

Can someone be patient and gentle enough to explain step by step what to do in order to connect to my wi-fi? I had no problems with windows finding the router.

Thanks in advance.

---

### Post by wildmanne39 on 2011-07-09
> **niko001 said:**
> I installed the latest Ubuntu on my ACER AspireONE as I had some issues with Windows. Installation done with no problem but I have no internet connection. As I am new to UBUNTU I do not know how to configure the intenet connection.

Can someone be patient and gentle enough to explain step by step what to do in order to connect to my wi-fi? I had no problems with windows finding the router.

Thanks in advance.Hi, do you have a wire connection? Please run these commands in a terminal one at a time
```
sudo lshw -C network
```
```
lspci -nn
```
```
iwconfig
```
```
lsmod
```
and post the outcome  here by clicking on new reply and click # and paste the information between the brackets.

---

### Post by niko001 on 2011-07-11
Thanks for the reply but I will ask a stupid question...where shall I type the codes? Do I have to connect directly the router to the netbook?

---

### Post by Surendil on 2011-07-11
On a terminal window.

ALT-F2 execution programs
type XTERM

be aware that the command SUDO will ask for root password, it should be the same passwd as your user passwd.

---

### Post by niko001 on 2011-07-14
Problem solved as I managed to connect through cable and downloaded the driver for the wi-fi

---


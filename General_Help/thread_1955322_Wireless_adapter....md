---
title: "Wireless adapter..."
date: 2012-04-09
forum: General Help
---

### Post by Fxy on 2012-04-09
Hi folks...

Just recently installed ubuntu on a "dell dimension 5000" but as of its ages has no wireless card install.  Instead of buying & fitting a wireless card i went ahead & bought a "MicroNEXT [ MN-WD550M ]" wireless usb dongle instead from ebay.  My problem is that the device is not recognised therefore not working.  I have downloaded a driver via the internet on a macbook & then transferred it over via usb.  The install was "8.04" and i had to run a list of commands in terminal to get the device up & running.  This had to be done every time i powered on the machine !!  Once i got connected to the internet i upgraded to "9.10" but as of every time i power on the machine now the previously successful commands no longer succeed :?  Can anyone please tell me how i can install the driver so that it works out of the box every time i power on the machine :?  The driver is labeled "rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100625" if that could be of any use !!



Thanks...  ...Fxy

---

### Post by Fxy on 2012-04-10
Anyone got any ideas :?

---

### Post by bogan on 2012-04-10
Hi!, **Fxy**.

We need to know the WiFi chipset the WD550M adapter uses; What does lsusb show? > sudo lsusb | grep etwork

If you install 11.10, the rtl8712usb driver is in the download.

Chao!,** bogan**

---

### Post by Fxy on 2012-04-10
> **bogan said:**
> Hi!, **Fxy**.

We need to know the WiFi chipset the WD550M adapter uses; What does lsusb show? 

If you install 11.10, the rtl8712usb driver is in the download.

Chao!,** bogan**



Hope this can be of any help ;-)

furycd001@security-van-112:~$ sudo lsusb | grep etwork
[sudo] password for furycd001: 
furycd001@security-van-112:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 004 Device 002: ID 046d:c016 Logitech, Inc. M-UV69a/HP M-UV96 Optical Wheel Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 0bda:8171 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 1bcf:0c31 Sunplus Innovation Technology Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
furycd001@security-van-112:~$ 

Fxy...

---

### Post by kiirokurisu on 2012-04-10
None of those USB devices are wireless adapters, according to Google. Try unplugging the device, then plugging it back, and immediately running ```
dmesg | tail
```.

---

### Post by Runthantrip on 2012-04-11
did you use ndiswrapper at all in that list of commands you mentioned?
 I was having the same problem with having to load my drivers manually after start up, but [post 41]("http://www.ubuntuforums.org/showthread.php?t=1805830&page=5") helped me.  i tried both methods but only the second method seemed to stick.i have not had a problem with it since and it loads at start up.

---

### Post by gandaran on 2012-04-11
do a clean install of ubuntu 11.10 or 12.04, those realtek drivers are provided on ubuntu from 10.10 and up making that wireless adapter work out of the box, on older ubuntu versions you will have to install compiling tools first to compile the driver, not easy!

---

### Post by bogan on 2012-04-11
Hi!, **Fxy**,

You posted:```
 lsusb .....Bus 001 Device 005: [COLOR=DarkRed]ID 0bda:8171[/COLOR] Realtek Semiconductor Corp....
```"[COLOR=DarkRed]ID 0bda:8171"[COLOR=Black] is the ID 0f the Realtek [COLOR=Blue]RTL8188SU[/COLOR] WLan USB WiFi Adapter for which the[COLOR=Blue] rt8712usb[/COLOR] is the correct driver. [ I use one myself without problems with 11.10.]

Disregard kiirokorisu's comment, - his Google search went amiss, - but +1 to his request for you to post [/COLOR][/COLOR]```
dmesg | tail 
```[COLOR=DarkRed][COLOR=Black]and also for installing 11.10.

Chao!, **bogan**.
[/COLOR][/COLOR]

---

### Post by kiirokurisu on 2012-04-11
My bad... I saw Realtek and presumed they don't make any Wifi chipsets. Learn something new every day!

---

### Post by Fxy on 2012-04-11
Thanks for the replies everyone :-}. Looks like I may just upgrade to solve my problem...  ... I don't really like unity, but I can live with it like if it solves my wifi problems

---

### Post by gandaran on 2012-04-11
> **Fxy said:**
> Thanks for the replies everyone :-}. Looks like I may just upgrade to solve my problem...  ... I don't really like unity, but I can live with it like if it solves my wifi problems
if you don't like unity don't use it! the solution is easy, first install ubuntu then install another desktop environment from software center, you can have ubuntu look and feel like any other linux distribution, gnome shell or ubuntu classic are just two of the options available.

---

### Post by Fxy on 2012-04-12
> **gandaran said:**
> if you don't like unity don't use it! the solution is easy, first install ubuntu then install another desktop environment from software center, you can have ubuntu look and feel like any other linux distribution, gnome shell or ubuntu classic are just two of the options available.

Thank for the help everyone.  Upgrading done the job :-}. But since I don't like unity I've just installed openbox & xfce instead :-p}

---


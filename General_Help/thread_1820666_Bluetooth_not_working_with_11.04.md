---
title: "Bluetooth not working with 11.04"
date: 2011-08-07
forum: General Help
---

### Post by trapline91 on 2011-08-07
I recently got a new laptop ( Acer Aspire 4730z ) which has bluetooth capabilities; however, bluetooth doesn't seem to be detected in 11.04. I'm not sure what to do about it honestly. Was hoping someone knew.

---

### Post by maxar6 on 2011-08-07
Do you have a bluetooth client setup?

---

### Post by trapline91 on 2011-08-07
I only have what came with the default install of 11.04. I figured it has to do with the linux kernel, so I'm not sure where to go from there.

---

### Post by pjd99 on 2011-08-07
Are you running all the latest updates? For me, bluetooth broke on the upgrade to 11.04 but started working a few weeks ago when updates came through...

It might start working if, once you're logged in, you open a terminal and:
```

sudo service bluetooth restart

```That used to be enough to get bluetooth working, but would have to delete and re-add the device (BT mouse) for it to communicate.

---

### Post by trapline91 on 2011-08-08
Restarting the service doesn't seem to help either. Maybe I should try a custom kernel?

---

### Post by pjd99 on 2011-08-08
Hmmm. What do you get if you run the following command:
```

lsusb | grep Bluetooth

```If nothing, can you just post the results of:
```

lsusb

```

---

### Post by scratch22 on 2011-08-09
Same issue on a Acer aspire 5750g (LX.RCGR2.073)... [http://www.acer.com.au/ac/en/AU/content/model/LX.RCG02.073](http://www.acer.com.au/ac/en/AU/content/model/LX.RCG02.073)

It has bluetooth 3 capatbilites (apparently)... Bluetooth driver appears to be there... /etc/bluetooth/main.conf 

sudo services bluetooth restart.. works fine

> stopping bluetooth
> starting bluetooth

But inside the System > Preferences > Bluetooth panel says "Bluetooth adapter not detected"

I just bought this lappy yesterday because my HP DV7 decided that 1.5 years was enough time it was going to give me for my cash, the graphics driver fried itself... pretty typical apparently... 

But on that system I installed Ubuntu 11.04 fine without hassle and bluetooth worked straight up off fresh install..

Im wondering if its the Bluetooth 3? or Acer hardware conf...??

Hope this might help... really dont wont to have to buy an external adapter...

---

### Post by davidsrsb on 2011-08-12
My desktop was working with an external Cliptec adaptor on 11.04 until about a week ago. Now the device is detected, but fails to accept the usb address properly. I think a recent dbus update may be responsible

---

### Post by sumith_p on 2011-08-25
Hi....i am using acer aspire 5750g ci3 2gb......ubuntu 11.04 64 bit....

sumith@sumith-Aspire-5750:~$ lsusb | grep Bluetooth
sumith@sumith-Aspire-5750:~$ lsusb
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 064e:c21c Suyin Corp. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

i am getting this by giving those commands....still bluetooth program says ...bluetooth adapter not detected.....as mentioned by SCRATCH22

sudo services bluetooth restart.. works fine

> stopping bluetooth
> starting bluetooth

But inside the System > Preferences > Bluetooth panel says "Bluetooth adapter not detected"

What to do....?

---

### Post by adam.g.pullen on 2011-09-18
Hello Everyone,

+1 for having same problem as sumith_p. Same M/C same Ubuntu version only 32 bit.

Thanks

---

### Post by rezbd on 2011-09-18
I have same problem on my SAMSUNG NF108-A01 netbook. blutetooth isn't detected on Lubuntu 11.04. after running this command 

lsusb | grep Bluetooth
it shows **Bus 003 Device 004: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)**

---

### Post by anur.bhargav on 2011-09-18
Following the below methods to might resolve the problem.

Remove current bluez without remove depends packages
```
sudo dpkg -P –force-depends bluez
```

Download bluez for Ubuntu 10.10
```
wget https://launchpad.net/ubuntu/+source/bluez/4.69-0ubuntu2/+build/1930179/+files/bluez_4.69-0ubuntu2_i386.deb
```

Install bluez
```
sudo dpkg -i bluez_4.69-0ubuntu2_i386.deb
```

If Ur problem gets solved:popcorn:, and please make sure u don't update the Bluetooth package anytime during the next system update

---

### Post by sumith_p on 2011-09-18
> **anur.bhargav said:**
> Following the below methods to might resolve the problem.

Remove current bluez without remove depends packages
```
sudo dpkg -P –force-depends bluez
```

Download bluez for Ubuntu 10.10
```
wget https://launchpad.net/ubuntu/+source/bluez/4.69-0ubuntu2/+build/1930179/+files/bluez_4.69-0ubuntu2_i386.deb
```

Install bluez
```
sudo dpkg -i bluez_4.69-0ubuntu2_i386.deb
```

If Ur problem gets solved:popcorn:, and please make sure u don't update the Bluetooth package anytime during the next system update
Hi i removed bluez.....using

sudo apt-get remove bluez


i downloaded the i386 package..now i am not able to install it since i am running amd64.....
what to do....?

---

### Post by gandaran on 2011-09-18
> **sumith_p said:**
> Hi i removed bluez.....using

sudo apt-get remove bluez


i downloaded the i386 package..now i am not able to install it since i am running amd64.....
what to do....?
install bluez from package manager
```
sudo apt-get install bluez
```
also install blueman, blueman works better to turn on bluetooth device.
and check that bluetooth is enabled in BIOS if blueman cannot turn on bluetooth.

---

### Post by sumith_p on 2011-09-18
yep i installed.....amd64 packages for ubuntu 10.10...but it didnt work...now i went back to latest bluez....i have installed blueman....when i run it it says
bluez daemon not running..
when i click blue tooth it says....it cant detect any blue tooth adapter..my laptop is acer aspire 5750...is it due to bluetooth 3.0

---

### Post by gandaran on 2011-09-18
> when i click blue tooth it says....it cant detect any blue tooth adapter..my laptop is acer aspire 5750...is it due to bluetooth 3.0
did you check in BIOS if bluetooth is enabled?

---

### Post by sumith_p on 2011-09-18
how can i check that....i cant see anything mentioned about bluetooth in bios
....

---

### Post by anur.bhargav on 2011-09-19
I thought i should have put this earlier.. but anyways here what u should for the 64Bit version.
```
wget http://launchpadlibrarian.net/54171397/bluez_4.69-0ubuntu2_amd64.deb
```

---

### Post by sumith_p on 2011-09-23
haah...finally bluetooth is working for me....installing older bluetooth version didnt do me any good..This thread helped....me...
[http://ubuntuforums.org/showthread.php?t=1667631](http://ubuntuforums.org/showthread.php?t=1667631)
i renamed the file mentioned in the thread then again changed to original....
i really dont know what happened now its working....!!!!
thank you guys for all the help

---


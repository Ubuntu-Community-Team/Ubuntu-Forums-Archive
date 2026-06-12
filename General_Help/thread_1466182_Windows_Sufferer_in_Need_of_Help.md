---
title: "Windows Sufferer in Need of Help"
date: 2010-04-30
forum: General Help
---

### Post by helloblaine on 2010-04-30
I'm running the latest release of Ubuntu on a separate partition and I haven't been able to connect to wireless internet on it.

I would like to solely run Ubuntu, if only I could get the internet to run.
 I have an hp laptop, it's a dv4 1220us model. I currently see a few lines representing wifi with an exclamation point beside it. I need a step-by-step walking through of how to connect to the wireless internet in the house. Please be patient with me, as I am new to Ubuntu. I would really appreciate any help I may receive.
Thank you in advance and I hope to hear from some of you with your advice. :)

---

### Post by chessnerd on 2010-04-30
Left click on the WiFi icon, go to your houses' WiFi network (whatever it is named) and then enter the password (if it has one). That should connect it.

---

### Post by dino99 on 2010-04-30
right now i'm googling around your hardware, into a terminal, let me know about :

sudo lshw -C network
ifconfig
lspci | grep Wireless
sudo iwlist scanning

---

### Post by helloblaine on 2010-04-30
I'll try this, though I think I would have already. Haha

I don't think my wireless network card is working correctly in ubuntu, though it does in windows 7.

---

### Post by helloblaine on 2010-04-30
I have to restart to switch over, but I'll tell you what happens.

---

### Post by helloblaine on 2010-04-30
> **dino99 said:**
> right now i'm googling around your hardware, into a terminal, let me know about :

sudo lshw -C network
ifconfig
lspci | grep Wireless
sudo iwlist scanning


Ok, every line was responsive except "sudo iwlist scanning"
It responded with "Interface doesn't/does not support scanning".

---

### Post by dino99 on 2010-04-30
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

[https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)

[http://wwww.ubuntuforums.org/showthread.php?t=1456310](http://wwww.ubuntuforums.org/showthread.php?t=1456310)

---

### Post by helloblaine on 2010-04-30
So I need to do the first set of lines to figure out what wireless card I have, and then install the appropriate driver from the ubuntu website? 
How do I get it over to my ubuntu partition without there being internet on it? 

And then once that is accomplished, I just click and connect to my internet?

---

### Post by chessnerd on 2010-04-30
You'll probably want an Ethernet cable to connect without WiFi (or, if you have a second computer, work with that one connected to the Internet) so that you can be inside Ubuntu to work this out. It seems like a bit of a Catch22 (and it is) but you can't really work out how to fix an Internet connection without access to the Internet...

---

### Post by helloblaine on 2010-04-30
I have a mac I can respond from and an sd card to transfer files :P Haha 

Apparently I have a Broadcom Corporation BCM4322 wireless card, I believe I got the appropriate driver onto the linux partition, now how do I install it? Haha

---

### Post by chessnerd on 2010-04-30
> **helloblaine said:**
> I have a mac I can respond from and an sd card to transfer files :P Haha 

Apparently I have a Broadcom Corporation BCM4322 wireless card, I believe I got the appropriate driver onto the linux partition, now how do I install it? Haha

Likely it is a .run file, so you'll need to make it executable by going to the command-line, moving to the directory with the file, then type "chmod +x filename" without the quotes where "filename" is the name of the file. Then type "./filename" again, without the quotes and it should execute the file.

If the file is not a .run file let me know the extension and/or give me the website that you got it from so I can take a look at the type of file.

---

### Post by helloblaine on 2010-04-30
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

I downloaded the 64 bit one, and it's a .tar.gz file.

---

### Post by chessnerd on 2010-04-30
> **helloblaine said:**
> [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

I downloaded the 64 bit one, and it's a .tar.gz file.

Hold the phones.

I read the README file and it said that Ubuntu has the drivers in its repos. Open Synaptic under System>Administration and type broadcom. I believe boardcom-sta-common is the driver package. Click and mark for installation.

Good thing I read things...

---

### Post by dino99 on 2010-04-30
goto synaptic and install: bcmwl-modaliases

(system --> admin --> synaptic)

---

### Post by chessnerd on 2010-04-30
> **dino99 said:**
> goto synaptic and install: bcmwl-modaliases

I believe that's installed by default (it is on mine) but wouldn't that mean he could go under System>Administration>Hardware Drivers and use that to get his driver then?

Blaine, if you want, you can try that. It might work.

I should have suggested that in the first place, instead I said to "left click the WiFi icon" as if you wouldn't have thought of that already...

---

### Post by cariboo on 2010-04-30
My netbook has a bcm4312 chipset, when I went to System->Administration->Hardware drivers, both Broadcom drivers were listed there, the b43 and sta.

---

### Post by dino99 on 2010-04-30
have you wifi and wire both plugged ? if so try without wire to see if bcm is detected.

if you have still trouble, install hostapd

---

### Post by helloblaine on 2010-05-02
So, I bought an ethernet cable at my work(best buy) and plugged it in, immediately it popped up and told me to install the wireless drivers. :D 

It works, and I am now a penguin. ;D

---


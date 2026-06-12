---
title: "Wireless not working on Acer Aspire One"
date: 2010-05-17
forum: General Help
---

### Post by weebulseco on 2010-05-17
in compliance with bonekracker's advice, i have reposted my SOS. i have the result of the outputs of the commands for ifconfig, iwconfig, and etc.. i have uploaded it in the file[ output.doc.]("http://www.simpack.cjb.net/output.doc") i hope this would be helpful in debugging my problem.

but before that, i do notice that if i click on the icon for the Network Manager, the Wireless networks is set to 'wireless disabled'. maybe if i can make it turn on, my wireless problem will be solved.. its just that i even if i move the switch for the wifi, it still wouldn't turn on..

thanks again..

---

### Post by wilee-nilee on 2010-05-17
Does the network manager show the same from a live Cd or usb, (however you loaded Ubuntu onto the aspire). I have a aod250 and have never had a wireless problem, but I lost the Ethernet port so it will be going back to them for a warranty repair. Which model do you have?

---

### Post by weebulseco on 2010-05-17
gz5 model with the 8GB of ssd.
unfortunately, it's been out of warranty already.

---

### Post by nothingspecial on 2010-05-17
You have an atheros card. You may have more luck with the madwifi drivers.

[[COLOR="Magenta"]Here[/COLOR]]("http://ubuntuforums.org/showpost.php?p=9304657&postcount=1") is a simple copy and paste how to.

---

### Post by weebulseco on 2010-05-17
thanks nothingspecial, i'll try it.

---

### Post by Peter09 on 2010-05-17
Are you running Lucid? My aspire one (same model as you) worked straight out of the box. Check that the hardware wireless switch is not Off.

---

### Post by wilee-nilee on 2010-05-17
> **Peter09 said:**
> Are you running Lucid? My aspire one (same model as you) worked straight out of the box. Check that the hardware wireless switch is not Off.

That was my first thought but didn't ask.

---

### Post by dandnsmith on 2010-05-17
Looking in the output.doc, I didn't see anything to suggest that it was recognising the atheros wireless - no driver loaded.

I had this problem back with (I think ) Ubuntu 7.x (I used the Windows driver with ndis...), but then it went away with a later version. Curiously, the parallel version of Mint worked out of the box.

Another oddity concerned turning on/off the wireless - if I had it on with Windows and then booted Ubuntu it was working, and if off with Windows then it was off with Ubuntu (the switch had no effect with Ubuntu).

I think there are postings with solutions on the AAO forums - these may well be up-to-date as far as getting a working solution is concerned.

I don't have a 'permanent' linux on the AAO, as my wife won't allow me to 'mess it up', so it has all been done with linux booted from USB-stick

HTH

---

### Post by weebulseco on 2010-05-17
> **Peter09 said:**
> Are you running Lucid? My aspire one (same model as you) worked straight out of the box. Check that the hardware wireless switch is not Off.

i'm running Ubuntu Netbook Remix 10.04

@nothingspecial: have followed the link you suggested.. i'll have to try the wifi tomorrow since i don't have wifi in my house. :-)

cheers everyone, thanks for your help..

---

### Post by nothingspecial on 2010-05-17
One thing that how to (reading it again, may have forgotten).

```
sudo nano /etc/modprobe.d/blacklist-ath_pci.conf
```

Put a comment # infront of blacklist ath_pci if you have problems.

---

### Post by weebulseco on 2010-05-17
> **nothingspecial said:**
> One thing that how to (reading it again, may have forgotten).

```
sudo nano /etc/modprobe.d/blacklist-ath_pci.conf
```Put a comment # infront of blacklist ath_pci if you have problems.

forgive my ignorance with ubuntu/linux system (being a newbie and and all that), but i can't find the line of code you are referring to for the 
```
sudo nano /etc/modprobe.d/blacklist-ath_pci.conf
```

am trying the netbook now but i just can't seem to connect with the wifi in this coffee shop.
my laptop can connect, but my netbook can't. i also notice that the pilot light (LED) for the wifi is not lighted. switching it manually doesn't turn it on. am getting desperate with this netbook..

---

### Post by BslBryan on 2010-05-17
> **weebulseco said:**
> forgive my ignorance with ubuntu/linux system (being a newbie and and all that), but i can't find the line of code you are referring to for the 
```
sudo nano /etc/modprobe.d/blacklist-ath_pci.conf
```

am trying the netbook now but i just can't seem to connect with the wifi in this coffee shop.
my laptop can connect, but my netbook can't. i also notice that the pilot light (LED) for the wifi is not lighted. switching it manually doesn't turn it on. am getting desperate with this netbook..

He means open up a terminal and type in that command.  However, I would change that to ```
gksudo gedit /etc/modprobe.d/blacklist-ath_pci.conf
```

It will open up a document in a text editor with something like:
blacklist pcspkr
blacklist nv
blacklist....
etc.  
He suggests adding a # in front of the words ```
blacklist ath_pci
``` and seeing if that helps any.

Also, this trick served me well in Jaunty, but I'm not even sure the wl module ships with Lucid - worth a try anyway:
```
sudo rmmod ssb
sudo modprobe wl
```

And if that doesn't work, remove the drivers you have currently and run this command
```
jockey-gtk
```
This graphical program will probe your computer for hardware and match it up with correct drivers, which when selected, will be installed for you.

---

### Post by weebulseco on 2010-05-17
is it necessary that the unit be connected to the internet to do all that?

---

### Post by BslBryan on 2010-05-17
Only the last command, the program jockey-gtk, requires the internet.

---

### Post by krimzonstarr on 2010-05-17
Hi,
I have an AAO ZG5 with the 160gb HD. I also use the Atheros card, and works out of the box with Karmic and Lucid with wifi. 

I have noticed that the wifi killswitch does not always register when the system is running. Often it will take a networkmanager restart or a full reboot cycle to register. If I remember correctly, when I first installed Ubuntu on this netbook about 18 months ago, the switch defaulted to off when I was finished installation. Usually, tripping the switch a few times and a few reboots will get me back to the "on" status. Without an on-screen indicator, it is hard to tell what the switch position is.

That said, with you running a LiveUSB version, I do not know if the reboots will help your situation. I am sorry, but I would just suggest looking around the forums more. I really do love Ubuntu on my AAO, and I have been windows free since I bought it.

If the wife doesn't allow you to do a full installation, how about wubi? This would not change the partitions on your AAO, while allowing you most of the benefits of a full install.

Good luck!

---

### Post by weebulseco on 2010-05-17
> **BslBryan said:**
> Only the last command, the program jockey-gtk, requires the internet.

thanks, i'll try that one too later..

---

### Post by weebulseco on 2010-05-17
woohaa!! finally, the wifi is functioning. am able to connect to the internet, although the pilot lite for the wifi is still off. no matter, the important thing is that it's working already..

special thanks go out to nothingspecial and BslBryan. thank you very much for the help and patience. 

:-D

---


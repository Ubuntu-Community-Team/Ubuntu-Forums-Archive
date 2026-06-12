---
title: "Help installing Belkin wireless adaptor f5d7000"
date: 2006-03-18
forum: General Help
---

### Post by ade234uk on 2006-03-18
I dont think the earlier thread is helping so here I go again.

I am trying to get my Belkin Wireless PCI adaptor card working in Ubuntu.

1) I have checked the device manager and it is there.

2) The make of the card is a Belkin f5d7000 version 2000. This is what the sticker says on the card
The chipset is Broadcom BCM4306

3) I installed the .inf file using the following command sudo ndiswrapper - i bcmwl5.inf

4) Then I enter the following command sudo ndiswrapper -l to list and it tells me that bcmwl5 is an invalid driver. So I presume I have the wrong .inf file

5) I then try to remove this using the following command sudo ndiswrapper -e bcmwl5.inf but it says it does not exist weird

6) When I look in etc/ndiswrapper directory I see a folder called bcmwl5 

Ok so now for the questions.
I need to find the correct .inf for my wireless card. It is a Belkin f5d7000 version 2000, this is what the sticker says. Has anyone else got one of these cards and made it work in Ubuntu

Once I have found this I then need to know how I install this .inf file again and if there is anything else I need to do.

I am nearly there and getting the wireless working with Ubuntu would be fantastic

---

### Post by Steve1961 on 2006-03-18
[QUOTE=ade234uk]I dont think the earlier thread is helping so here I go again.

I am trying to get my Belkin Wireless PCI adaptor card working in Ubuntu.

1) I have checked the device manager and it is there.

2) The make of the card is a Belkin f5d7000 version 2000. This is what the sticker says on the card
The chipset is Broadcom BCM4306

3) I installed the .inf file using the following command sudo ndiswrapper - i bcmwl5.inf

4) Then I enter the following command sudo ndiswrapper -l to list and it tells me that bcmwl5 is an invalid driver. So I presume I have the wrong .inf file

5) I then try to remove this using the following command sudo ndiswrapper -e bcmwl5.inf but it says it does not exist weird

6) When I look in etc/ndiswrapper directory I see a folder called bcmwl5 

Ok so now for the questions.
I need to find the correct .inf for my wireless card. It is a Belkin f5d7000 version 2000, this is what the sticker says. Has anyone else got one of these cards and made it work in Ubuntu

Once I have found this I then need to know how I install this .inf file again and if there is anything else I need to do.

I am nearly there and getting the wireless working with Ubuntu would be fantastic[/QUOTE]

Try this page for the correct drivers:

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#B](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#B)

Update:  I've just remembered an issue I had with one of these cards some time ago.  Although it said version 2 on the box the output of lspci -v said it was version 3.  So I installed the bcmwl5a.inf driver supplied by Dell for version 3, and available from the above link, and everything worked fine.

---

### Post by ade234uk on 2006-03-19
I maganed to uninstall the ndiswrapper and then the ndiswrapper folder in etc/  and started again.

I also made sure I had some other files as I was just using .inf file. I then made sure that I was in the correct directory before installing. Once I did this I tried the ndiswrapper -i {inffile} command and this time it worked. I then went to administration >> network and I can now see the wlan as one of my networking options so I have activated it.

All I need to do now is try to get a connection.

---

### Post by Steve1961 on 2006-03-19
[QUOTE=ade234uk]I maganed to uninstall the ndiswrapper and then the ndiswrapper folder in etc/  and started again.

I also made sure I had some other files as I was just using .inf file. I then made sure that I was in the correct directory before installing. Once I did this I tried the ndiswrapper -i {inffile} command and this time it worked. I then went to administration >> network and I can now see the wlan as one of my networking options so I have activated it.

All I need to do now is try to get a connection.[/QUOTE]


try typing the following in a terminal:

> sudo dhclient wlan0

---

### Post by ade234uk on 2006-03-19
It looks like my card antenna is dead. About 5 months ago this card was being used on OSX and suddenly it was stop getting a signal from the router. I even installed and uninstalled in OSX without any luck and it would still not work.

The same is applying to Ubuntu, even thou it is being recognised and the drivers are correctly installed and the power light comes on after entering modprobe blah blah in the terminal I am still not picking up any signal. 

I have tried this command above without any luck. I have checked numerous other settings and still no luck.

I think I have a dodgy antenna or something internally wrong with the card. I dont want to spend money on a new antenna to find this does not solve the problem so I have gone 50/50 on a new card with my brother that is supposed to actually work natively in Ubuntu. 

This card is a Linksys WMP54G Wireless-G PCI Adapter

---

### Post by Steve1961 on 2006-03-19
[QUOTE=ade234uk]It looks like my card antenna is dead. About 5 months ago this card was being used on OSX and suddenly it was stop getting a signal from the router. I even installed and uninstalled in OSX without any luck and it would still not work.

The same is applying to Ubuntu, even thou it is being recognised and the drivers are correctly installed and the power light comes on after entering modprobe blah blah in the terminal I am still not picking up any signal. 

I have tried this command above without any luck. I have checked numerous other settings and still no luck.

I think I have a dodgy antenna or something internally wrong with the card. I dont want to spend money on a new antenna to find this does not solve the problem so I have gone 50/50 on a new card with my brother that is supposed to actually work natively in Ubuntu. 

This card is a Linksys WMP54G Wireless-G PCI Adapter[/QUOTE]


Given the problems you've had before it does sound like your card is the problem.  I've not used the card you've bought but you should be able to get it up and running with a native driver or ndiswrapper.

---

### Post by ricperry1 on 2007-01-17
Try this site:

[http://madwifi.org/wiki/UserDocs/Distro/Ubuntu](http://madwifi.org/wiki/UserDocs/Distro/Ubuntu)

It seems like you just need to install the restricted modules.  You can see if your card is supported by MADWiFi driver here:  

[http://madwifi.org/wiki/Compatibility#Belkin](http://madwifi.org/wiki/Compatibility#Belkin)

Cheers,
Rich

---


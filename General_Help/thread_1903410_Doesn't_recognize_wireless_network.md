---
title: "Doesn't recognize wireless network"
date: 2012-01-02
forum: General Help
---

### Post by nlions88 on 2012-01-02
I'm a new Ubuntu user as of about 45 minutes ago so please bear with me.

I just installed Ubuntu on my laptop and want to connect to the internet wirelessly.  For whatever reason though, my wireless network isn't showing up on the list under "Wireless".  I know it's not a problem with the network, because I am connected to it wirelessly on my second desktop.. which is how I'm typing this thread right now.

I've gone through the Ubuntu help documents and it says I should

> Click the NetworkManager icon in the system notification area.

I feel like a complete idiot because the above means absolutely nothing to me.  I don't know what the system notification area is and I've been searching for it but can't find it, hence I am unable to locate this "NetworkManager" icon.

I have found that my wireless network isn't on the list by going to System > Preferences > Network Connections.  However, I don't even know if this is the right place, confusing me even more.

Any help is greatly appreciated as so far this seems like an overwhelming leap from Windows.

---

### Post by gandaran on 2012-01-02
your network should show up on the panel network icon list if drivers are installed, most wireless chipsets are supported on ubuntu, some aren't like broadcom brand chipsets and need to install the drivers, find out the wireless chipset brand and model then we can help you, post the output of this command
```
sudo lshw -C network
```
this will tell us all about the wireless card

---

### Post by nlions88 on 2012-01-02
Okay I copied this into a text file and put it on a flash drive.  I don't know what kind of formatting will be lost with the transition of this on my Windows...


[sudo] password for alex: 
  *-network               
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f69fc000-f69fffff
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 13
       serial: 00:23:ae:30:61:50
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.23 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:29 memory:f68fc000-f68fffff ioport:de00(size=256)
alex@alex-laptop:~$


Also could anyone tell me where this system notification area is so I can stop feeling completely clueless?

---

### Post by gandaran on 2012-01-02
> lso could anyone tell me where this system notification area is so I can stop feeling completely clueless?
which ubuntu version do you have?
the notification area is the network panel icon on the right side.
> description: Network controller
product: BCM4312 802.11b/g
you may want to look in additional drivers to activate the broadcom driver, must be connected with wired internet or follow this guide for broadcom drivers
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#STA%20-%20No%20Internet%20access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#STA%20-%20No%20Internet%20access)

---

### Post by audiomick on 2012-01-02
A dumb question that needs to be asked: Has the laptop a hardware switch for the wireless, and is it switched on? ;)

---

### Post by nlions88 on 2012-01-02
I am using Ubuntu 9.10

---

### Post by nlions88 on 2012-01-02
> **audiomick said:**
> A dumb question that needs to be asked: Has the laptop a hardware switch for the wireless, and is it switched on? ;)

The F2 key doubles as a hotkey to turn the wireless on and off in Windows but it doesn't appear to do anything for Ubuntu.

---

### Post by gandaran on 2012-01-02
> **nlions88 said:**
> The F2 key doubles as a hotkey to turn the wireless on and off in Windows but it doesn't appear to do anything for Ubuntu.
only when broadcom drivers are installed then you can switch on/off

---

### Post by gandaran on 2012-01-02
> **nlions88 said:**
> I am using Ubuntu 9.10
recommend you upgrade to either ubuntu 10.04 or 11.10 as 9.10 isn't supported anymore.

---

### Post by nlions88 on 2012-01-02
> **gandaran said:**
> recommend you upgrade to either ubuntu 10.04 or 11.10 as 9.10 isn't supported anymore.

How am I supposed to update without an internet connection?

---

### Post by nlions88 on 2012-01-02
Okay I don't know if this is useful or not..

I used the nm-tool command and it told me

State: disconnected

However it then said

Type: wired

I don't understand this, I have never used a wired connection for my laptop.

---

### Post by audiomick on 2012-01-02
It defaults to a wired connection if it can't find a wireless one, I think.

Can you connect with a cable and get a CD organised to move to 10.04 LTS or 11.10? This may make it easier for you to get the drivers you appear to be missing.

---

### Post by nlions88 on 2012-01-02
I'll try and do this but I'm not sure if I have any blank CDs.

---

### Post by TyeS on 2012-01-02
I am very new to Ubuntu and I haven't had problems with my internet connection via wireless until I plugged my friend's wired internet into the computer. I was connected for a while and then when I rebooted the computer I was asked to type in a password which has never been needed to start the computer. When I went to open the wicd network it asked for a password also/ sometimes now it will just show the icon in the dock as if it's opening then disappear.


the message I get is: [COLOR="Red"]Could not connect to wicd's D-Bus interface. Check the wicd log for error messages.[/COLOR]

I looked up how to check the wicd log but when I got to the [COLOR="red"]var/log/wicd[/COLOR] the folder icon had an "x" on it and the folder is empty.

I also read a forum where they said to check the [COLOR="red"]etc/init.d/wicd[/COLOR]

and the forum had the proper scripts to replace it with. However when I tried to put the correct scripts in I got this message:

[COLOR="red"]Could not save the file /etc/init.d/wicd. You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again.[/COLOR]

I also tried going to the [COLOR="red"]"/etc/wicd/wired-settings.conf"[/COLOR] but when I do the [COLOR="red"]manager-settings.conf[/COLOR] has an "x", [COLOR="red"]wired-settings.conf [/COLOR]has an "x" and the [COLOR="red"]wireless-settings.conf[/COLOR] has an "x" on them and cannot be opened. 

Does anyone know how to fix this problem? I am extremely new to Ubuntu and very confused.

---

### Post by cortman on 2012-01-02
> **TyeS said:**
> I am very new to Ubuntu and I haven't had problems with my internet connection via wireless until I plugged my friend's wired internet into the computer. I was connected for a while and then when I rebooted the computer I was asked to type in a password which has never been needed to start the computer. When I went to open the wicd network it asked for a password also/ sometimes now it will just show the icon in the dock as if it's opening then disappear.


the message I get is: [COLOR="Red"]Could not connect to wicd's D-Bus interface. Check the wicd log for error messages.[/COLOR]

I looked up how to check the wicd log but when I got to the [COLOR="red"]var/log/wicd[/COLOR] the folder icon had an "x" on it and the folder is empty.

I also read a forum where they said to check the [COLOR="red"]etc/init.d/wicd[/COLOR]

and the forum had the proper scripts to replace it with. However when I tried to put the correct scripts in I got this message:

[COLOR="red"]Could not save the file /etc/init.d/wicd. You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again.[/COLOR]

I also tried going to the [COLOR="red"]"/etc/wicd/wired-settings.conf"[/COLOR] but when I do the [COLOR="red"]manager-settings.conf[/COLOR] has an "x", [COLOR="red"]wired-settings.conf [/COLOR]has an "x" and the [COLOR="red"]wireless-settings.conf[/COLOR] has an "x" on them and cannot be opened. 

Does anyone know how to fix this problem? I am extremely new to Ubuntu and very confused.

Start your own thread- don't hijack someone else's.

---

### Post by TyeS on 2012-01-02
I was looking for the option to start my own but I couldn't find the option to start my own thread.

---

### Post by cortman on 2012-01-02
> **TyeS said:**
> I was looking for the option to start my own but I couldn't find the option to start my own thread.

Sure- in the "Absolute Beginner" forum, there's a button on the upper left that says "New Thread". Try that one and we'll be glad to help you!

---

### Post by cotcot on 2012-01-02
> **nlions88 said:**
> How am I supposed to update without an internet connection? Hopefully for you in the same way as you got this message on the forum.
The Broadcom chip is not supported in 9.10 out of the box. 
There are other posts on this subject. [[COLOR="Blue"]Here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1309760&page=3") is one. I hope you can get there. I do not think you will be able to solve the problem without downloading something.

---

### Post by TyeS on 2012-01-02
Thank you. Sorry for jumping in here.

---

### Post by gandaran on 2012-01-02
> **TyeS said:**
> I am very new to Ubuntu and I haven't had problems with my internet connection via wireless until I plugged my friend's wired internet into the computer. I was connected for a while and then when I rebooted the computer I was asked to type in a password which has never been needed to start the computer. When I went to open the wicd network it asked for a password also/ sometimes now it will just show the icon in the dock as if it's opening then disappear.


the message I get is: [COLOR="Red"]Could not connect to wicd's D-Bus interface. Check the wicd log for error messages.[/COLOR]

I looked up how to check the wicd log but when I got to the [COLOR="red"]var/log/wicd[/COLOR] the folder icon had an "x" on it and the folder is empty.

I also read a forum where they said to check the [COLOR="red"]etc/init.d/wicd[/COLOR]

and the forum had the proper scripts to replace it with. However when I tried to put the correct scripts in I got this message:

[COLOR="red"]Could not save the file /etc/init.d/wicd. You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again.[/COLOR]

I also tried going to the [COLOR="red"]"/etc/wicd/wired-settings.conf"[/COLOR] but when I do the [COLOR="red"]manager-settings.conf[/COLOR] has an "x", [COLOR="red"]wired-settings.conf [/COLOR]has an "x" and the [COLOR="red"]wireless-settings.conf[/COLOR] has an "x" on them and cannot be opened. 

Does anyone know how to fix this problem? I am extremely new to Ubuntu and very confused.
run these commads to fix the d-bus error 
```
sudo dpkg-reconfigure wicd
```
```
sudo update-rc.d wicd defaults
```
then reboot PC, also why use wicd? doesn't network manager work even better?

---

### Post by MARP1961 on 2012-01-02
Let's get back to helping **nlions88** shall we?

Nlions88, you really need to do a fresh install of Ubuntu using a currently supported version. I would recommend the current version 11.10 Oneiric Ocelot.

Your Broadcom wireless needs a driver to install once you are connected to internet via an ethernet cable.

If you get a current version of Ubuntu and an ethernet connection help will be easier to give.

---

### Post by TyeS on 2012-01-02
The network manager won't open.

---


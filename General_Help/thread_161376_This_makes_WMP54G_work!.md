---
title: "This makes WMP54G work!"
date: 2006-04-16
forum: General Help
---

### Post by Cullen Schaffer on 2006-04-16
There are lots of posts on this forum about people having problems getting a Linksys WMP54G wireless card to work with Ubuntu.  Up until half an hour ago I was one of them.  There are dozens of suggestions to follow up, many of which are contradictory and/or highly technical.  I finally happened on this one, which (unlike the others) worked and didn't require any specialized networking knowledge.

I'm reposting this for two reasons.  First, because I hope it will help the next person will get to the answer that works quicker than I did.  Second, because neither I nor the original poster understand why this works and I, for one, would like to know.  I'll appreciate enlightenment from anyone on what's going on, and particularly why the commands need to be repeated.

Thanks in advance.

And now, here's the original post:

I'm using this script with breezy 5.10 Ubuntu, no probs. Only: You have to use the commands for the initialisation twice (therefore two "loops"), don't know why. I made it simple and copied the lines.

I changed nothing in Ubuntu. It works out of the box with this script. Don't use the network-gui. The gui doesn't work. This setting is for WPA with AES and DHCP. The passphrase must be in ascii-text. I don't like it but only this way works for me. Don't know why too.

<code>
#!/bin/sh
echo "WMP54G with rt2500-Driver"
ifconfig ra0 up
echo "network is starting"

iwpriv ra0 set NetworkType=Infra
iwpriv ra0 set AuthMode=WPAPSK
iwpriv ra0 set EncrypType=AES
iwpriv ra0 set WPAPSK="mypasswd"
iwpriv ra0 set SSID="myssid"

echo "First loop: waiting for connection"
sleep 5
dhclient -q ra0
iwlist scanning

echo "WMP54G with rt2500-Treiber"
ifconfig ra0 up
echo "network is starting"

iwpriv ra0 set NetworkType=Infra
iwpriv ra0 set AuthMode=WPAPSK
iwpriv ra0 set EncrypType=AES
iwpriv ra0 set WPAPSK="mypasswd"
iwpriv ra0 set SSID="myssid"

echo "Second loop: waiting for connection"
sleep 5
dhclient -q ra0
iwlist scanning
</code>

---

### Post by bionnaki on 2006-04-16
I have a wmp54g as well and replacing /etc/network/interfaces with:

> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0

iface ra0 inet dhcp
pre-up iwconfig ra0 essid ***
pre-up iwconfig ra0 mode managed
pre-up iwpriv ra0 set Channel=*
pre-up iwpriv ra0 set AuthMode=WPAPSK
pre-up iwpriv ra0 set EncrypType=AES
pre-up iwpriv ra0 set WPAPSK="***********"
pre-up iwpriv ra0 set TxRate=0




auto ra0


does the trick for me.
what is the difference between what I do and your trick?
thanks!

---

### Post by bionnaki on 2006-04-16
...oh, and for future reference, here's how to set up a static ip using my method:

> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0

iface ra0 inet static
address 192.168.1.***
netmask 255.255.255.0
gateway 192.168.1.1
pre-up iwconfig ra0 essid *****
pre-up iwconfig ra0 mode managed
pre-up iwpriv ra0 set Channel=****
pre-up iwpriv ra0 set AuthMode=WPAPSK
pre-up iwpriv ra0 set EncrypType=AES
pre-up iwpriv ra0 set WPAPSK="*****"
pre-up iwpriv ra0 set TxRate=0



auto ra0

---

### Post by k420 on 2006-05-11
the first script that was posted here what should i name the file and how do i activate it

---

### Post by bionnaki on 2006-05-19
no idea...use use my method (editing /etc/network/interfaces). works flawlessly.

---

### Post by bieber on 2006-06-07
How would I modify this for WEP instead of WPA?  And should it work with the WUSB54G as well? (Same card, just USB, I'm assuming)

---

### Post by bionnaki on 2006-06-08
no idea

---

### Post by BigWillieLL66 on 2006-06-12
I'm completely new to this OS or any Linux OS.  Could someone tell me exactly how and where to enter all this.  I really want to use and explore this OS more, but without internet access it's worthless to me.  Thanks in advance.

---

### Post by bionnaki on 2006-06-12
open up the terminal 
and enter your name + password

type "sudo gedit /etc/network/interfaces" without the quotation marks

delete everthing listed
and copy/paste what we have written above.
save, exit, reboot

---

### Post by bionnaki on 2006-06-12
be sure to change the *** with whatever info works for you.

---

### Post by BigWillieLL66 on 2006-06-12
Thanks.  I'll give that a try.  Hopefully I'll be making my next post from Firefox on Ubuntu.

---

### Post by inuyasharox4776 on 2006-06-13
[QUOTE=bionnaki]open up the terminal 
and enter your name + password

type "sudo gedit /etc/network/interfaces" without the quotation marks

delete everthing listed
and copy/paste what we have written above.
save, exit, reboot[/QUOTE]
i get a GTK error when using the command sudo gedit /etc/network/interfaces . how do I fix this?

---

### Post by bionnaki on 2006-06-13
gtk error? what does it say?
do you have gedit installed? does it open normally?

try sudo gedit

should pop up.

if not, you can always use another editor
try 

sudo nano /etc/network/interfaces

---

### Post by inuyasharox4776 on 2006-06-13
whoops...i dont have WMP54G, I have WUSB54G.

---

### Post by bionnaki on 2006-06-13
what driver does that use? if it uses rt2500, it should work.

---

### Post by Deinonych on 2006-06-13
[QUOTE=bionnaki]I have a wmp54g as well and replacing /etc/network/interfaces with:



does the trick for me.
what is the difference between what I do and your trick?
thanks![/QUOTE]

Wonderful!  That works perfectly, and with a non-broadcasting SSID to boot.  Thank you for posting this!

---

### Post by inuyasharox4776 on 2006-06-14
edit:
i fixed that problem, not i have another. The only place my wusb54g is appearing is in device manager, and nowhere else. any fix for this?

---

### Post by cquarinto on 2006-06-16
Hi Bionnaki, I am going to try and use your method in a few minute. 
BTW - gedit from the terminal doesn't work. It complains with  

"cannot open display: (null)"

I'll try in a few minutes and let you know if the trick works.

---

### Post by cquarinto on 2006-06-16
This didn't work for me !! The name of the device on the card is WMP54GV1
I will try tomorrow night with NDSI Wrapper, unless somebody comes with a different solution. Thanks
:confused:

---

### Post by SleepyHollow on 2006-06-18
[QUOTE=Cullen Schaffer]There are dozens of suggestions to follow up, many of which are contradictory and/or highly technical.  I finally happened on this one, which (unlike the others) worked and didn't require any specialized networking knowledge.

And now, here's the original post:

I'm using this script with breezy 5.10 Ubuntu, no probs. Only: You have to use the commands for the initialisation twice (therefore two "loops"), don't know why. I made it simple and copied the lines.

I changed nothing in Ubuntu. It works out of the box with this script. Don't use the network-gui. The gui doesn't work. This setting is for WPA with AES and DHCP. The passphrase must be in ascii-text. I don't like it but only this way works for me. Don't know why too.

<code>
#!/bin/sh
echo "WMP54G with rt2500-Driver"
ifconfig ra0 up
echo "network is starting"

iwpriv ra0 set NetworkType=Infra
iwpriv ra0 set AuthMode=WPAPSK
iwpriv ra0 set EncrypType=AES
iwpriv ra0 set WPAPSK="mypasswd"
iwpriv ra0 set SSID="myssid"

echo "First loop: waiting for connection"
sleep 5
dhclient -q ra0
iwlist scanning

echo "WMP54G with rt2500-Treiber"
ifconfig ra0 up
echo "network is starting"

iwpriv ra0 set NetworkType=Infra
iwpriv ra0 set AuthMode=WPAPSK
iwpriv ra0 set EncrypType=AES
iwpriv ra0 set WPAPSK="mypasswd"
iwpriv ra0 set SSID="myssid"

echo "Second loop: waiting for connection"
sleep 5
dhclient -q ra0
iwlist scanning
</code>[/QUOTE]

Hello,

I don't mind using and reposting of my script but it would be kind to give with it my nickname or a [link to the original post]("http://ubuntuforums.org/showthread.php?t=108791&highlight=iwpriv+ra0+set+WPAPSK%3D%22mypasswd%22"). 

:roll:

---

### Post by Pwnd on 2006-08-24
Can you please elaborate on the astricts on what they're supposed to be.  

;)  Thanks.

---

### Post by dragonlor20 on 2006-08-24
> **bionnaki said:**
> I have a wmp54g as well and replacing /etc/network/interfaces with:



does the trick for me.
what is the difference between what I do and your trick?
thanks!

Your method seems to be taking me back to the computer hanging up on the network interfaces initialization... Im not sure why that is?

Glad i backed up /etc/network/interfaces... I guess I will try the start-up script now...

---

### Post by annuschka on 2006-09-04
I tried the scripts. That wasnt a good idea, it seems.
I've got Kubuntu 6.06.1. Now even the cable-ethernet-network-device gives me a "Error while listing network interfaces: Could not parse XML output from the network configuration backend" when I try to enable it in the system settings/network settings. How can I "undo" the scripts? I dont want to reinstall kubuntu :???: 
And yes, I'm new to all of this. Its my third day with kubuntu... *confused*

---

### Post by NeoGreen on 2006-09-11
I tried the first script posted and I rebooted and it didn't work.  Was I supposed to have installed the driver first or is this script supposed to work without the driver.  Sort of like plug and play for Windows???[LIST]
[/LIST]

---


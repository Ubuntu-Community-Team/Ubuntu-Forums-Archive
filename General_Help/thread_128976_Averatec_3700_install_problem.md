---
title: "Averatec 3700 install problem"
date: 2006-02-12
forum: General Help
---

### Post by drachir on 2006-02-12
I want to install ubuntu 5.10 on an averatec 3700. I tried the live cd and it booted fine with the exception of the video and I found how to fix that on the install. Thanks forums!

Here is my problem. The laptop came with Win backup already preinstalled on a seperate partition (using 7.8g on a 80g hdd), so I cleared the 71g to install ubuntu. I created a swap of 512 and am using the rest of the drive for ubuntu. The install goes fine until after I create a user name and password. 

Then it freezes on Configuring apt screen at 25%. 
Any suggestions? Ubuntu is the best distro I have tried, this is the only problem I have come up with that I haven't seen on the forums. 

Thanks everyone

---

### Post by drachir on 2006-02-12
well I got the install but my wireless doesnt work. Anyone else have any of these issues

---

### Post by nanotube on 2006-02-12
well, if you could post what your wireless card is, maybe we can come up with some ideas. :)

---

### Post by drachir on 2006-02-12
how would I find out what my wireless is?

---

### Post by drachir on 2006-02-12
RT2500 wireless

---

### Post by drachir on 2006-02-12
ok I got the wireless to work. this help out extremely.

[https://wiki.ubuntu.com/WifiDocs/RalinkRT2500/DriverAndRaconfig#dontneed](https://wiki.ubuntu.com/WifiDocs/RalinkRT2500/DriverAndRaconfig#dontneed)
The one thing I noticed about ubuntu that wasnt there with other distros was the help. The people who post how to's and quick start guides make it understandable. Clearly ubuntu will be the best most used distro.

---

### Post by solracarevir on 2006-12-11
just for the record:

in order to use the internal wireless you need to insert \\Option		"DisableIRQ"\\ on the device section of your xorg.conf, for example:

 	Code:
 	[LEFT]Section "Device"
	Identifier	"VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter"
	Driver		"via"
	BusID		"PCI:1:0:0"
#the next line is the one you need to add
Option		"DisableIRQ" 
EndSection[/LEFT]
 
on my averatec (av3715) you have to keep the wireless switch on the "off" position for the wireless to work propertly. After instaling ubuntu on mine I was connected to my wifi on less than 5 minutes!:razz:

---

### Post by mrfuzzemz on 2007-04-13
I've been trying to install Edgy or Feisty on a 3700, but everything is very slow (windows redrawing).  What do you do to get the install going?

---

### Post by kommaanda on 2007-04-24
mrfuzzemz,
I have been experiencing the same problem on my Averatec 3250. The live cd boots up and all rendering as well as mouse movements are slow. Then, I installed fesity with the alternate install cd. The first time I logged in everything was normal. Only my ethernet/internet access wasn't working. I tried to change stuff in the network manager (icon on top right side of the screen (which actually said that I was connected) it went back to slow rendering/useless mouse. Do you have Internet access when experiencing these issues?

---

### Post by mrfuzzemz on 2007-04-24
I've not even had it load enough for me to really test it.  I've read if you add this line:
> Option "DisableIRQ"
To your via section in xorg.conf that wireless networking runs better.

---


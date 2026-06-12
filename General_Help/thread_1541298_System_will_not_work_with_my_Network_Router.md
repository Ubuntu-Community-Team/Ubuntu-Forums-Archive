---
title: "System will not work with my Network Router"
date: 2010-07-29
forum: General Help
---

### Post by XXXTURBO6 on 2010-07-29
First of all i'm new here and Hello!
 
Tonight I had a friend talk me into UBUNTU and he gave me his disc to up-load, He said his lap top comunicated with his wireless router just fine after the restart. Well mine didn't and now the old Windows stuff is gone and the new UBUNTU will not comunicate with my wireless router. 
 
Why did his work just fine and mine not?
 
What do I do from here so it will connect?
 
 
 
Thanks,
xxxturbo6

---

### Post by bazzal1941 on 2010-07-29
Which version of Ubuntu?

How are you trying to connect, no key, wep or wpa?

---

### Post by choochoousmc on 2010-07-29
> **XXXTURBO6 said:**
> First of all i'm new here and Hello!
 
Tonight I had a friend talk me into UBUNTU and he gave me his disc to up-load, He said his lap top comunicated with his wireless router just fine after the restart. Well mine didn't and now the old Windows stuff is gone and the new UBUNTU will not comunicate with my wireless router. 
 
Why did his work just fine and mine not?
 
What do I do from here so it will connect?
 
 
 
Thanks,
xxxturbo6
For a better response from those with the knowledge, more info would be needed.
Off shelf notebook or desktop or custom built?
brand and model  What kind of hardware in it  etc.

# 1 you really should of made a set of windows reinstall disks first and backed up your data.
#2  Remember Murphy's Law. If something can go wrong, it will and when it does, it will do the most damage.

Now to your problem.
If the install worked right, at top of the sceen in the main menu bar you should have a network manager (ubuntu 10.04 lts) looks like a series of arches one on top of another.
If you have this, right click it to open the properties.
You may have to manually enter some info on your routers IP address.
Also if your router was password protected, you may have to enter it manually.
Now if you don't have UBUNTU 10.04 lts, I would suggest you get it. Either order the disk (free) or download the ISO image.
Also in the main menu  you will see  (??) applications, places, systems
click systems  then preferences then network connections that may help you
or   systems  then administration  hardware drivers  or network tools
This is the current and latest supported version.
It took two tries for me to be up and running.
Once you are I think you will like it better than windows.
Many things are similar some are different.
I think it is easier than windows and smoother and faster and overall more stable.
Been using it for 2 months.
I've had minor issues and gotten lots of help here and learned as I went.

---

### Post by Jazzy_Jeff on 2010-07-29
One of the first things you should do is plug your computer into your router and do all the updates. This could fix any problems that are going on.

---

### Post by XXXTURBO6 on 2010-07-29
> **bazzal1941 said:**
> Which version of Ubuntu?
 
How are you trying to connect, no key, wep or wpa? It's a COMPAQ laptop...
 
It's UBUNTU 10.04 
 
and trying to connect (WPA personal)
 
 
The UBUNTU 10.04 up-load worked fine, Now I just need to be able to connect to my wireless router and then I think everything will work fine.
 
I now have found ALL my wireless router info that I written down previously so what & where do I need to go to type this info in?
 
 
PS: Just so you guy's know this is my first time ever trying this UBUNTU stuff and have no idea where stuff is or anything so please excuse me if I need to be walked through this by hand.. LOL

---

### Post by P4man on 2010-07-29
You cant connect or the wifi card isnt recognized?
If you right click on the network manager (network icon top right), do you get a "enable wireless" option and is it turned on? Does your laptop have a hardware switch or a keyboard combination to turn wifi on/off, and if so, have you tried that (then check again if wireless is activated).

If that doesnt help; open a terminal (applications > accessoiries > terminal) and type in these two commands:

```
lsusb
```

```
lspci
```

Those will list all your hardware. Find a line that contains "wireless network controller" or "802.11 B/G" something along those lines and report the exact type here.

---

### Post by bumanie on 2010-07-29
Please do what P4man has asked for - that will help a lot. Also, can you state the brand and model of router, ie if it is a win only modem, you will probably have to resort to using ndiswrapper and the windows .inf file. I have a compaq that works fine on wireless and also with a 3g modem (bit of mucking around with the 3g at times). Supply the requested outputs of the commands and router brand etc. and someone should be able to help.

---

### Post by XXXTURBO6 on 2010-07-29
> **bumanie said:**
> Please do what P4man has asked for - that will help a lot. Also, can you state the brand and model of router, ie if it is a win only modem, you will probably have to resort to using ndiswrapper and the windows .inf file. I have a compaq that works fine on wireless and also with a 3g modem (bit of mucking around with the 3g at times). Supply the requested outputs of the commands and router brand etc. and someone should be able to help. 
Router brand is **LinkSys model# WRT54G V8**
 
Lap top is a **Compaq model # HSTNN-C17C**
 
**Note:** Ever since I re-started the lap top my Blue WIFI icon/button will not light up when pressed. It did light up on the initial boot up or up load but now will not work after a re-start.
 
 
I will try to enter those commands that P4man asked and get back with the findings,
 
First of all where do I enter those commands? Is it in the bar on the page when I try to pull up firefox?
 
 
 
Last night I entered the commands as the result of a search. Below is what I entered and the results.
 
 
**Entered: /var/lib/NetworkManager/NetworkManager.state**
 
[COLOR=blue]**Results: [main]**        (Exactly what they are supossed to be)[/COLOR]
 
[COLOR=red]NetworkingEnabled=true[/COLOR]
[COLOR=red]WirelessEnabled=true[/COLOR]
[COLOR=red]WWANEEnabled=true             [/COLOR]
 
 
 
**Entered: /etc/NetworkManager/nm-system-settings.conf**
 
[COLOR=blue]**Results:**        (supposed to be "true" instead of FALSE)[/COLOR]
 
[COLOR=blue][main][/COLOR]
[COLOR=red]plugins=ifupdown,keyfile[/COLOR]

[COLOR=blue][ifupdown][/COLOR]
[COLOR=red]managed=**FALSE** (Supposed to be= **True**)[/COLOR]

---

### Post by XXXTURBO6 on 2010-07-29
> **P4man said:**
>  You cant connect or the wifi card isnt recognized?  Not sure! The WIFI light on my lap top used to work right after the up-load now after the re-start it won't, even pressing the button it will not come on..
 
> **P4man said:**
>  If you right click on the network manager (network icon top right), do you get a "enable wireless" option and is it turned on?  No the "enable wireless" isn't there.
 
 
> **P4man said:**
>  Does your laptop have a hardware switch or a keyboard combination to turn wifi on/off, and if so, have you tried that (then check again if wireless is activated). It has a WIFI button that you just press to turn it on/off and it is supposed to light up when on. After the initial upload it was lit up and then after a re-start it was off and not it won't even turn on/light up when pressed.
 
> **P4man said:**
> If that doesnt help; open a terminal (applications > accessoiries > terminal) and type in these two commands:
 
```
lsusb
```
 
```
lspci
```
 
Those will list all your hardware. Find a line that contains "wireless network controller" or "802.11 B/G" something along those lines and report the exact type here.  BTW How do you "Open a terminal"?? 
 
I will try to enter these commands now and get back with the results of each.
 
 
Thank you!
xxxturbo6

---

### Post by P4man on 2010-07-29
> **XXXTURBO6 said:**
>  BTW How do you "Open a terminal"?? 


Just like I explained in the part between ()'s.

---

### Post by endotherm on 2010-07-29
the terminal can be found from Applications -> Accessories -> Terminal

you will find that most support for unix'y operating systems like ubuntu are given in terminal commands for several reasonsk. everyones desktop is differant (but the command line is the same), and capturing, cropping, annotating and uploading screenshots for point and click instructions may take hours. 

BTW, the problem is not with your router, but with the card in your laptop. some of the posters on this thread are quite knowledgable, so they should be able to get you running. just to check, have you looked in System -> Administration -> Hardware drivers to see if ubuntu has a "restricted" driver for your device? if so, install it, and all may work itself out.

---

### Post by XXXTURBO6 on 2010-07-29
> **endotherm said:**
> the terminal can be found from Applications -> Accessories -> Terminal
 
you will find that most support for unix'y operating systems like ubuntu are given in terminal commands for several reasonsk. everyones desktop is differant (but the command line is the same), and capturing, cropping, annotating and uploading screenshots for point and click instructions may take hours. 
 
BTW, the problem is not with your router, but with the card in your laptop. some of the posters on this thread are quite knowledgable, so they should be able to get you running. just to check, have you looked in System -> Administration -> Hardware drivers to see if ubuntu has a "restricted" driver for your device? if so, install it, and all may work itself out. OKAY, Once I go to Applications -> Accessories -> Terminal  where do I type in the codes?
 
 
I have looked everywhere on this system and it is so different than what i'm used to NOTHING looks familiar and I have no clue how to navigate this hardware so you will have to please excuse my ignorance at the moment while trying to figure this all out..
 
Like for instance, I have no clue what a "terminal" is or even looks like so when you guy's mention that to me I have no clue what i'm even looking for.
 
You will have to basicly tell me what to do in Baby steps (so to speak) in order for you to walk me through this properly.. 
 
 
I have been writting this stuff on my office computer and copying the posts on paper then walking to my lap-top to figure this stuff out.. I'm trying......

---

### Post by XXXTURBO6 on 2010-07-29
> **P4man said:**
> You cant connect or the wifi card isnt recognized?
If you right click on the network manager (network icon top right), do you get a "enable wireless" option and is it turned on? Does your laptop have a hardware switch or a keyboard combination to turn wifi on/off, and if so, have you tried that (then check again if wireless is activated).
 
If that doesnt help; open a terminal (applications > accessoiries > terminal) and type in these two commands:
 
```
lsusb
```
 
```
lspci
```
 
Those will list all your hardware. Find a line that contains "wireless network controller" or "802.11 B/G" something along those lines and report the exact type here. OKAY, I figured out where to type the stuff in and there is "802.11 b/g"  listed  there.   
 
**[COLOR=blue][lsusb] RESULTS:[/COLOR]**
 
[COLOR=red]Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/COLOR]
[COLOR=red]Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/COLOR]
[COLOR=red]Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/COLOR]
[COLOR=red]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/COLOR]
 
 
 
**[COLOR=blue][lspci] RESULTS for a wireless network[/COLOR]**
 
[COLOR=red]*Network controler: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)[/COLOR]
[COLOR=red]*Ethernet controler: Realtek Semiconductor co., LTD RTL-8139/8139C/8139C+ (rev 10)[/COLOR]

---

### Post by P4man on 2010-07-29
> **XXXTURBO6 said:**
> O 
**[COLOR=blue][lspci] RESULTS for a wireless network[/COLOR]**
 
[COLOR=red]*Network controler: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)[/COLOR]
[COLOR=red]*Ethernet controler: Realtek Semiconductor co., LTD RTL-8139/8139C/8139C+ (rev 10)[/COLOR]


Excellent, thats exactly what we needed to know. You have a broadcom 4311 wireless card in that machine. You are going to need to install some stuff to make that work and for that its easiest if you have internet connection on that machine. Can you plug in a wired network cable temporarily to fix this? If not, we can also fix it buts its going to be a lot harder.

Everything you need to know is here:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20BCM43xx%20drivers](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20BCM43xx%20drivers)

But I imagine you may need some help with that, so let us know first if you can plug in a network cable to get on the internet or not.

---

### Post by XXXTURBO6 on 2010-07-29
> **P4man said:**
> Excellent, thats exactly what we needed to know. You have a broadcom 4311 wireless card in that machine. You are going to need to install some stuff to make that work and for that its easiest if you have internet connection on that machine. Can you plug in a wired network cable temporarily to fix this? If not, we can also fix it buts its going to be a lot harder.
 
Everything you need to know is here:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20BCM43xx%20drivers]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20BCM43xx%20drivers")
 
But I imagine you may need some help with that, so let us know first if you can plug in a network cable to get on the internet or not. Good! 
 
Now what is the best way to hook this lap top to my office desktop to get the internet?
 
Can I go and download this stuff I need onto a disc then transfer it in the lap top?
 
ndiswrapper shows the broadcom 4311 as a "WORKING" driver under ndiswrapper, Can I use my office computer to download ndiswrapper and then install that disc in UBUNTU?

---

### Post by jsyl on 2010-07-29
You don't have to necessarily get an ethernet cable.
Take a USB drive that you have, go on your other computer and download these drivers onto it: [http://ud-pc.com/driver/broadcom/broadcom_43xx_drv_4102284.zip](http://ud-pc.com/driver/broadcom/broadcom_43xx_drv_4102284.zip)
Put that zip file inside your USB drive, and then plug it into your laptop.
Before you transfer the file into your laptop, put your CD in the drive. Then go to "System --> Administration --> Software Sources"
On the bottom of that window, you'll see an option to enable the CDROM for software sources. Check that option.
Then, close Software Sources and press "close"
Go to "System --> Administration --> Synaptic Package Manager"
Type "ndis" into the search box on the top right
Check off "ndisgtk" and press "Apply" on the top. It will take this package off the CDROM
Once it's installed, close Synaptic and navigate back to Software Sources. Uncheck the CDROM, and take out the CDROM from your drive.
Then, transfer the file you downloaded earlier to your laptop, and right-click it and press "Extract Here". You'll find a new folder that appears on your desktop. Go to "System --> Administration --> Windows Wireless Drivers"(Which is installed with the "ndisgtk" package)
Press "Install" and navigate to the new folder that was created. Choose the file that finishes with ".inf". It will install the driver, and then you have to reboot.
Tell me how this works out for you.

---

### Post by P4man on 2010-07-29
> **XXXTURBO6 said:**
> ndiswrapper shows the broadcom 4311 as a "WORKING" driver under ndiswrapper, Can I use my office computer to download ndiswrapper and then install that disc in UBUNTU?

OH you have ndiswrapper installed? How did you manage that lol (no offense intended, its just that its not THAT easy and it typically requires internet connectivity which apparently you dont have?). 

Ndiswrapper lets you use windows drivers for wireless network cards. Its also a possibility, but if you use that you have to make sure you blacklist (disable) any native driver. Likewise if you are going with the above approach of installing a native linux driver, you have disable ndiswrapper.

Im guessing/hoping you tried mixing 2 solutions. Did you ever get a popup saying something about "restricted drivers" for your hardware (broadcom) and did you click the popup to install it?

---

### Post by XXXTURBO6 on 2010-07-29
> **jsyl said:**
> You don't have to necessarily get an ethernet cable.
Take a USB drive that you have, go on your other computer and download these drivers onto it: [http://ud-pc.com/driver/broadcom/broadcom_43xx_drv_4102284.zip](http://ud-pc.com/driver/broadcom/broadcom_43xx_drv_4102284.zip)
Put that zip file inside your USB drive, and then plug it into your laptop.
Before you transfer the file into your laptop, put your CD in the drive. Then go to "System --> Administration --> Software Sources"
On the bottom of that window, you'll see an option to enable the CDROM for software sources. Check that option.
Then, close Software Sources and press "close"
Go to "System --> Administration --> Synaptic Package Manager"
Type "ndis" into the search box on the top right
Check off "ndisgtk" and press "Apply" on the top. It will take this package off the CDROM
Once it's installed, close Synaptic and navigate back to Software Sources. Uncheck the CDROM, and take out the CDROM from your drive.
Then, transfer the file you downloaded earlier to your laptop, and right-click it and press "Extract Here". You'll find a new folder that appears on your desktop. Go to "System --> Administration --> Windows Wireless Drivers"(Which is installed with the "ndisgtk" package)
Press "Install" and navigate to the new folder that was created. Choose the file that finishes with ".inf". It will install the driver, and then you have to reboot.
Tell me how this works out for you. I Don't have a USB drive!
 
I do have several Ethernet cables though..
 
I ended up downloading the ndiswrapper drivers onto a cd from my office computer and went to install then into the lap top and I get this: Please insert the disc labled "Ubuntu 10.04 LTS_ Lucid Lynix_ -release i386 (20100429) in drive/cdrom/"
 
Would this be the same disc that I used to upload Ubuntu the first time?

---

### Post by XXXTURBO6 on 2010-07-29
> **P4man said:**
> OH you have ndiswrapper installed? How did you manage that lol (no offense intended, its just that its not THAT easy and it typically requires internet connectivity which apparently you dont have?). 
 
Ndiswrapper lets you use windows drivers for wireless network cards. Its also a possibility, but if you use that you have to make sure you blacklist (disable) any native driver. Likewise if you are going with the above approach of installing a native linux driver, you have disable ndiswrapper.
 
Im guessing/hoping you tried mixing 2 solutions. Did you ever get a popup saying something about "restricted drivers" for your hardware (broadcom) and did you click the popup to install it? Sorry for the confusion NO it's not installed, That is what it say's on the ndiswrapper page, it told me to look and see if my driver was a "Working" driver for ndiswrapper..  lol 
 
I am still trying to get the damn (ndiswrapper) CD that I burned to load/install on my lap top now and it keeps telling me to install the Ubuntu CD.... Mybe this Ubuntu thing wasn't for me, I guess I should have done a dual boot instead of a complete boot....

---

### Post by XXXTURBO6 on 2010-07-29
OKAY GUY'S, I have an Ethernet cable and I hooked it up to the lap top and the done a re-start. It will not let me log onto the internet and it's saying THE CONNECTION TIMED OUT and the pop up about "restricted drivers" came up and I tried to click on the broadcom driver to install and it won't let it.
 
PS: on the wireless connection at the top right it now shows "Auto etho-connection established" BUT it won't let me log onto firefox or internet explorer..... ???
 
 
 
 
 
SW.

---

### Post by XXXTURBO6 on 2010-07-29
Hope you guy's didn't give up on me, I think we were actually getting somewhere...
 
I have the ethernet cable pluged straight into the back of my Linksys and to the lap top and still not able to connect to the internet to do any uploading...
 
 
Any more suggestions?

---

### Post by endotherm on 2010-07-29
what is the output of 
```

nslookup www.ubuntuforums.org
ping -c3 www.ubuntuforums.org
sudo ifconfig
sudo route

```

---

### Post by XXXTURBO6 on 2010-07-29
> **endotherm said:**
> what is the output of 
```

nslookup www.ubuntuforums.org
ping -c3 www.ubuntuforums.org
sudo ifconfig
sudo route

```  Is this what your looking for?
 
**[nslookup **[**www.ubuntuforums.org**]("http://www.ubuntuforums.org")**]** 
 
**[COLOR=blue]RESULTS:[/COLOR]**
 
[COLOR=red]Server:  24.158.96.130[/COLOR]
[COLOR=red]Address: 24.158.96.130#53[/COLOR]
[COLOR=red][/COLOR] 
[COLOR=red]Non-authorative answer:[/COLOR]
[COLOR=red]Name: [/COLOR][[COLOR=red]www.ubuntuforums.org[/COLOR]]("http://www.ubuntuforums.org")
[COLOR=red]address: 91.189.94.12[/COLOR]
[COLOR=#ff0000][/COLOR] 
[COLOR=#ff0000][/COLOR] 
 **[ping -c3 **[**www.ubuntuforums.org**]("http://www.ubuntuforums.org")**]**
 
[COLOR=blue]**Results:**[/COLOR]
**[COLOR=#0000ff][/COLOR]** 
[COLOR=red]3 packets transmitted, 3 received, o% packet loss, time 2003ms [/COLOR]
[COLOR=red]rtt min/avg/mdev = 104.072/111.198/122.507/8.086 ms[/COLOR]
[COLOR=#ff0000][/COLOR] 
[COLOR=#ff0000][/COLOR] 
**[sudo ifconfig]**
 
**[COLOR=blue]RESULTS:[/COLOR]**
**[COLOR=#0000ff][/COLOR]** 
[COLOR=red][sudo] password for scot:[/COLOR]
[COLOR=#ff0000][/COLOR] 
[COLOR=#ff0000][/COLOR] 
**[COLOR=#000000][COLOR=black][[/COLOR]sudo route][/COLOR]**
 
**[COLOR=blue]RESULTS:[/COLOR]**
**[COLOR=#0000ff][/COLOR]** 
[COLOR=red][sudo] password for scot[/COLOR]

---

### Post by jsyl on 2010-07-29
When I said CDROM, I meant the original Ubuntu CDROM, that's what you insert after checking the option in Software Sources

---

### Post by endotherm on 2010-07-29
thats really weird. that you can ping an NSlookup indicates that the network is functioning, but a blank ifconfig and route would prevent that from being the case.
try running ifconfig and route without sudo and see if you get any output. 
if not, try 
```

sudo /etc/init.d/networking restart

``` and try again. 
failing that try:
```

sudo dhclient eth0

``` and see if you get output from ifconfig then.

---

### Post by P4man on 2010-07-29
> **XXXTURBO6 said:**
> 
**[COLOR=blue]RESULTS:[/COLOR]**
**[COLOR=#0000ff][/COLOR]** 
[COLOR=red][sudo] password for scot[/COLOR]

You have to enter your password there. Nothing will appear on screen, just type it in and hit enter to get the output of the command we want to see.

---

### Post by XXXTURBO6 on 2010-07-29
> **endotherm said:**
>  thats really weird. that you can ping an NSlookup indicates that the network is functioning, but a blank ifconfig and route would prevent that from being the case.
try running ifconfig and route without sudo and see if you get any output. 
if not, try 
```

sudo /etc/init.d/networking restart

```   **RESULTS:**  
[COLOR=red]*Reconfiguring network interfaces...[/COLOR]
[COLOR=red]Ignoring unknown interface eth0=eth0[/COLOR]
 
 
> **endotherm said:**
>  and try again. failing that try:
```
sudo dhclient eth0
``` and see if you get output from ifconfig then.  **RESULTS**:
 
[COLOR=red]Internet Systems Consortium DHCP Client V3.1.3[/COLOR]
[COLOR=red]Copyright 2004-2009 Internet Systems Consortium.[/COLOR]
[COLOR=red]All rights reserved.[/COLOR]
[COLOR=red]For info please visit [/COLOR][[COLOR=red]https://www.isc.org/software/dhcp/[/COLOR]]("https://www.isc.org/software/dhcp/")
[COLOR=red][/COLOR] 
[COLOR=red]Listening on LPF/eth0/00:16:d4:bc:28:b3[/COLOR]
[COLOR=red]Sending on LPF/eth0/00:16:d4:bc:28:b3[/COLOR]
[COLOR=red]DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8[/COLOR]
[COLOR=red]DHCPREQUEST of 192.168.1.103 on eth0 to 255.255.255.255 port 67[/COLOR]
[COLOR=red]DHCPACK of 192.168.1.130 from 192.168.1.1[/COLOR]
[COLOR=red]bound to 192.168.1.103 -- renewal in 34614 seconds.[/COLOR]

---

### Post by XXXTURBO6 on 2010-07-29
> **P4man said:**
> You have to enter your password there. Nothing will appear on screen, just type it in and hit enter to get the output of the command we want to see. Never knew I had to enter my pasword! lol  Thanks, It worked for the above results...

---

### Post by P4man on 2010-07-30
You need to type a password (once every 15 minutes I thnk) if you use "sudo" which executes a command as superuser. in fact you dont have to be superuser for some of these commands, but nevermind that.

So far your output looks completely okay. You got an IP address from the router, the DNS lookup works fine. Can you give us the output of 
```

route
```

Also can you open firefox and in the adress bar type in this:
```
http://[COLOR="Red"]74.125.77.104[/COLOR]
```

Does that bring up google homepage?

You are doing this at home right, not on a corporate network ?

---


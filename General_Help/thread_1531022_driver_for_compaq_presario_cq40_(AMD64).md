---
title: "driver for compaq presario cq40 (AMD64)"
date: 2010-07-14
forum: General Help
---

### Post by WitchBlade on 2010-07-14
where i can download all driver for my laptop HP compaq presario cq40 (amd64) ??

---

### Post by WitchBlade on 2010-07-14
> **WitchBlade said:**
> where i can download all driver for my laptop HP compaq presario cq40 (amd64) ??

can some1 suggest me what shud i install any driver for my laptop.. im just install ubuntu and i dont hve any any idea how to connect to internet

---

### Post by WitchBlade on 2010-07-14
hello... any1 know?

---

### Post by Twitch6000 on 2010-07-14
HP only supports linux to a point so it will be a hit and miss.

However linux has great hardware detection.

So if you can tell me what drivers you are needing installed. I can tell you how to get them.

Edit: oh and if you could open up a terminal and paste this command - lspci -n'

And post the results. It will help me help you.

---

### Post by WitchBlade on 2010-07-14
> **Twitch6000 said:**
> HP only supports linux to a point so it will be a hit and miss.

However linux has great hardware detection.

So if you can tell me what drivers you are needing installed. I can tell you how to get them.

Edit: oh and if you could open up a terminal and paste this command - lspci -n'

And post the results. It will help me help you.


i cant connect to the wireless internet.. i have graphic card ATI radeon..

---

### Post by Twitch6000 on 2010-07-14
> **WitchBlade said:**
> i cant connect to the wireless internet.. i have graphic card ATI radeon..

Well for your ATI graphics driver. Follow this guide - [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

For your wireless issue if you can post the results of lspci -n here I can help you further.

---

### Post by WitchBlade on 2010-07-14
> **Twitch6000 said:**
> HP only supports linux to a point so it will be a hit and miss.

However linux has great hardware detection.

So if you can tell me what drivers you are needing installed. I can tell you how to get them.

Edit: oh and if you could open up a terminal and paste this command - lspci -n'

And post the results. It will help me help you.

what u mean a terminal? how to get there? this command? --> - lspci -n'

---

### Post by Twitch6000 on 2010-07-14
Press alt+f2 and type gnome-terminal and press okay. that will bring you to the terminal.

---

### Post by WitchBlade on 2010-07-14
> **Twitch6000 said:**
> Press alt+f2 and type gnome-terminal and press okay. that will bring you to the terminal.

ok..1 minutes.. need to switch to win 7..i use dual os

---

### Post by Twitch6000 on 2010-07-14
> **WitchBlade said:**
> ok..1 minutes.. need to switch to win 7..i use dual os

No you need to do this in ubuntu for the command to work.

---

### Post by WitchBlade on 2010-07-14
0:00.0 0600: 1022:9600
00:01.0 0604: 103c:9602
00:04.0 0604: 1022:9604
00:05.0 0604: 1022:9605
00:06.0 0604: 1022:9606
00:07.0 0604: 1022:9607
00:11.0 0106: 1002:4391
00:12.0 0c03: 1002:4397
00:12.1 0c03: 1002:4398
00:12.2 0c03: 1002:4396
00:13.0 0c03: 1002:4397
00:13.1 0c03: 1002:4398
00:13.2 0c03: 1002:4396
00:14.0 0c05: 1002:4385 (rev 3a)
00:14.1 0101: 1002:439c
00:14.2 0403: 1002:4383
00:14.3 0601: 1002:439d
00:14.4 0604: 1002:4384
00:18.0 0600: 1022:1300 (rev 40)
00:18.1 0600: 1022:1301
00:18.2 0600: 1022:1302
00:18.3 0600: 1022:1303
00:18.4 0600: 1022:1304
01:05.0 0300: 1002:9612
01:05.1 0403: 1002:960f
08:00.0 0880: 197b:2382
08:00.2 0805: 197b:2381
08:00.3 0880: 197b:2383
08:00.4 0880: 197b:2384
09:00.0 0280: 14e4:4315 (rev 01)
0a:00.0 0200: 10ec:8136 (rev 02)

---

### Post by WitchBlade on 2010-07-14
im use..

broadcom 802.11g - wireless 

Realtek RTL8102E/RTL8103E Family PCI-E Fast Ethernet NIC (NDIS 6.20) - LAN

---

### Post by Twitch6000 on 2010-07-14
Ahh okay you have a broadcom wireless. BCM4312 802.11b/g LP-PHY

And according to the debain driver detector it should have a driver.

To get the driver hook up to Ethernet or windows and download -

[http://packages.ubuntu.com/lucid/i386/b43-fwcutter/download](http://packages.ubuntu.com/lucid/i386/b43-fwcutter/download)

Just click a server nearest you 

After you download it,install it and then restart. Your wireless should then work.

---

### Post by WitchBlade on 2010-07-14
> **Twitch6000 said:**
> Ahh okay you have a broadcom wireless. BCM4312 802.11b/g LP-PHY

And according to the debain driver detector it should have a driver.

To get the driver hook up to Ethernet or windows and download -

[http://packages.ubuntu.com/lucid/i386/b43-fwcutter/download](http://packages.ubuntu.com/lucid/i386/b43-fwcutter/download)

Just click a server nearest you 

After you download it,install it and then restart. Your wireless should then work.

no need to setting up the wireless connection? 
how about the Realtek driver?

and how to install it?

---

### Post by Twitch6000 on 2010-07-14
> **WitchBlade said:**
> no need to setting up the wireless connection? 
how about the Realtek driver?

The realtek driver should already be installed. it is supported in the kernel.

Yes you will need to connect to your wireless network.

The icon for wireless is in the top right. Just find the network. Its like doing it in windows.

---

### Post by WitchBlade on 2010-07-14
i get this when i install the driver..


Error: Wrong architecture 'i386'

Utility for extracting Broadcom 43xx firmware
fwcutter is a tool which can extract firmware from various source files. It's written for BCM43xx driver files. 


is it only 17kb driver file size..?

---

### Post by Twitch6000 on 2010-07-14
> **WitchBlade said:**
> i get this when i install the driver..


Error: Wrong architecture 'i386'

Utility for extracting Broadcom 43xx firmware
fwcutter is a tool which can extract firmware from various source files. It's written for BCM43xx driver files. 


is it only 17kb driver file size..?

Oh you are on a 64bit machine. Here is the 64bit download - [http://packages.ubuntu.com/hardy/amd64/bcm43xx-fwcutter/download](http://packages.ubuntu.com/hardy/amd64/bcm43xx-fwcutter/download)

Its a little bit older,but should still do the trick.

---

### Post by WitchBlade on 2010-07-14
> **Twitch6000 said:**
> Oh you are on a 64bit machine. Here is the 64bit download - [http://packages.ubuntu.com/hardy/amd64/bcm43xx-fwcutter/download](http://packages.ubuntu.com/hardy/amd64/bcm43xx-fwcutter/download)

Its a little bit older,but should still do the trick.


ok.. trying

---

### Post by Twitch6000 on 2010-07-14
So.. whats the outcome?

---

### Post by WitchBlade on 2010-07-14
> **Twitch6000 said:**
> So.. whats the outcome?


still the same... cant see any availabe wireless network..

i found before u ask me to type lspci -n in terminal.. i saw wireless icon..but after i type lspci -n,the icon change to Lan Ico.. and it not change after i install driver and restart my laptop...

---

### Post by WitchBlade on 2010-07-14
> **Twitch6000 said:**
> Oh you are on a 64bit machine. Here is the 64bit download - [http://packages.ubuntu.com/hardy/amd64/bcm43xx-fwcutter/download](http://packages.ubuntu.com/hardy/amd64/bcm43xx-fwcutter/download)

Its a little bit older,but should still do the trick.

its not supported with my machine, perhaps..

---

### Post by Twitch6000 on 2010-07-14
> **WitchBlade said:**
> still the same... cant see any availabe wireless network..

i found before u ask me to type lspci -n in terminal.. i saw wireless icon..but after i type lspci -n,the icon change to Lan Ico.. and it not change after i install driver and restart my laptop...

Alright open a terminal and try this - sudo ifconfig wlan0 up then see if you can get on the internet. Or post the outcome here.

---

### Post by WitchBlade on 2010-07-14
> **Twitch6000 said:**
> Alright open a terminal and try this - sudo ifconfig wlan0 up then see if you can get on the internet. Or post the outcome here.

wlan0: ERROR while getting interface flags: No such device

---

### Post by WitchBlade on 2010-07-14
i want to offline.. tommorow we continue! 
i have an emergency..

---

### Post by Twitch6000 on 2010-07-14
Alright I found a more up to date driver - [http://packages.ubuntu.com/lucid/amd64/b43-fwcutter/download](http://packages.ubuntu.com/lucid/amd64/b43-fwcutter/download)

Download it to the home folder and then paste this in a terminal -

```
 cd
sudo b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o
tar xfvj broadcom-wl-4.150.10.5.tar.bz2
sudo b43-fwcutter --unsupported -w /lib/firmware broadcom-wl-4.150.10.5/driver/wl_apsta_mimo.o
sudo chmod o+rx /lib/firmware/b43 /lib/firmware/b43legacy
sudo ifconfig wlan0 up
```



You should then have internet. If you do not post the outcome.

oh and if you could post the results of running iwconfig in the terminal.

Edit: Alrighty

---

### Post by WitchBlade on 2010-07-15
> **Twitch6000 said:**
> Alright I found a more up to date driver - [http://packages.ubuntu.com/lucid/amd64/b43-fwcutter/download](http://packages.ubuntu.com/lucid/amd64/b43-fwcutter/download)
 
Download it to the home folder and then paste this in a terminal -
 
```
 cd
sudo b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o
tar xfvj broadcom-wl-4.150.10.5.tar.bz2
sudo b43-fwcutter --unsupported -w /lib/firmware broadcom-wl-4.150.10.5/driver/wl_apsta_mimo.o
sudo chmod o+rx /lib/firmware/b43 /lib/firmware/b43legacy
sudo ifconfig wlan0 up
```
 
 
 
You should then have internet. If you do not post the outcome.
 
oh and if you could post the results of running iwconfig in the terminal.
 
Edit: Alrighty
 
i hve installed the driver but still the same..
 
i also copy paste the code u gave in terminal and its say "cannot open input file wl_apsta-3.130.20.0.o" my Lan internet connection also not working..

---

### Post by WitchBlade on 2010-07-15
**[COLOR=red]iwconfig[/COLOR]**
 
result: 
 
lo  --------- no wireless extensions.
 
eth0 ------- no wireless extensions.

---

### Post by Twitch6000 on 2010-07-15
> **WitchBlade said:**
> **[COLOR=red]iwconfig[/COLOR]**
 
result: 
 
lo  --------- no wireless extensions.
 
eth0 ------- no wireless extensions.

Now that is odd.. it isn't showing the wlan0.

My only other idea would be trying this in the terminal.

```
 sudo ifup wlan0 
```

If that does not work I am out of ideas. So you will need to wait for someone else.

---

### Post by WitchBlade on 2010-07-16
i put the drivers at Home Folder and put the code u gave.. and do -->

```
cd
sudo b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o
tar xfvj broadcom-wl-4.150.10.5.tar.bz2
sudo b43-fwcutter --unsupported -w /lib/firmware broadcom-wl-4.150.10.5/driver/wl_apsta_mimo.o
sudo chmod o+rx /lib/firmware/b43 /lib/firmware/b43legacy
sudo ifconfig wlan0 up
```

the reslut is --> cannot open input file wl_apsta-3.130.20.0.o

---

### Post by WitchBlade on 2010-07-16
> **Twitch6000 said:**
> Now that is odd.. it isn't showing the wlan0.

My only other idea would be trying this in the terminal.

```
 sudo ifup wlan0 
```If that does not work I am out of ideas. So you will need to wait for someone else.


outcome -> Ignoring unknown interface wlan0-wlan0

---

### Post by WitchBlade on 2010-07-16
on my 'hardware drivers'... i can see the broadcom b43 there, and it says 'this drivers is not activate'..when i click the activate.. a warning popup show and says 'System error: installArchives() Failed'

---

### Post by WitchBlade on 2010-07-16
anyone here?

---

### Post by pedro6 on 2010-07-16
i have the same laptop my wifi works fine, however when i push the f12 button (it enables and disables wifi) it comes up with some error. so if u push f12 so the light goes white then restart the computer i find that fixes it, i don't know if it is the same problem as your having though.

---

### Post by Twitch6000 on 2010-07-16
> **WitchBlade said:**
> on my 'hardware drivers'... i can see the broadcom b43 there, and it says 'this drivers is not activate'..when i click the activate.. a warning popup show and says 'System error: installArchives() Failed'

In order to use that driver you would need to have internet or the ubuntu dvd. However you already have the driver installed so there is no need.

---

### Post by WitchBlade on 2010-07-16
> **Twitch6000 said:**
> In order to use that driver you would need to have internet or the ubuntu dvd. However you already have the driver installed so there is no need.

yes.. i have wireless internet right now but can't see any signal from it..

---

### Post by WitchBlade on 2010-07-16
> **pedro6 said:**
> i have the same laptop my wifi works fine, however when i push the f12 button (it enables and disables wifi) it comes up with some error. so if u push f12 so the light goes white then restart the computer i find that fixes it, i don't know if it is the same problem as your having though.

what version ubuntu n wireless driver u use?

---

### Post by WitchBlade on 2010-07-16
> **pedro6 said:**
> i have the same laptop my wifi works fine, however when i push the f12 button (it enables and disables wifi) it comes up with some error. so if u push f12 so the light goes white then restart the computer i find that fixes it, i don't know if it is the same problem as your having though.

this f12 not work.. when i press it, nothing happen

---

### Post by WitchBlade on 2010-07-17
> **pedro6 said:**
> i have the same laptop my wifi works fine, however when i push the f12 button (it enables and disables wifi) it comes up with some error. so if u push f12 so the light goes white then restart the computer i find that fixes it, i don't know if it is the same problem as your having though.

can u tell me what version of ubuntu u use? and where u download the driver?

---

### Post by WitchBlade on 2010-07-17
ok.. i found the problem here, i think..

when i install the driver

i got this..

[B]FAILED TO INSTALL PACKAGES "B43-fwcutter_012-1build1_amd64.deb"
[/B]
```
(*Reading database...113466 files and directories currently installed)*
Preparing to replace b43-fwcutter 1:012-1build1. (using ...B43 fwcutter_012-1build1.amd64.deb)
unpacking replacement b43-fwcutter...
setting up b43-fwcutter (1:012-1build1)...
-- 2010-07-18 07:42:29 -- http://downloads.openwrt.org/sources/wl.apsta_3.130.20.0.o

Resloving downloads openwrt.org..... Failed: name or service not known
wget: unable to resolve host address 'downloads.openwrt.org'
dpkg: error processing b43-fwcutter ( --install--)
subprocess installed post-installation script returned error exit status 1

processing triggers for man-db
error were encountered while processing: b43-fwcutter

```

looks like need internet connection to complete this driver installation... or need other drivers.. :)

---

### Post by WitchBlade on 2010-07-17
im also get the msg which ask me to report the problem error.. when i click the 'report' it says im use 'not geniune ubuntu package'... :((

---

### Post by WitchBlade on 2010-07-18
> **WitchBlade said:**
> ok.. i found the problem here, i think..

when i install the driver

i got this..

[B]FAILED TO INSTALL PACKAGES "B43-fwcutter_012-1build1_amd64.deb"
[/B]
```
(*Reading database...113466 files and directories currently installed)*
Preparing to replace b43-fwcutter 1:012-1build1. (using ...B43 fwcutter_012-1build1.amd64.deb)
unpacking replacement b43-fwcutter...
setting up b43-fwcutter (1:012-1build1)...
-- 2010-07-18 07:42:29 -- http://downloads.openwrt.org/sources/wl.apsta_3.130.20.0.o

Resloving downloads openwrt.org..... Failed: name or service not known
wget: unable to resolve host address 'downloads.openwrt.org'
dpkg: error processing b43-fwcutter ( --install--)
subprocess installed post-installation script returned error exit status 1

processing triggers for man-db
error were encountered while processing: b43-fwcutter

```looks like need internet connection to complete this driver installation... or need other drivers.. :)


anybody know?

---


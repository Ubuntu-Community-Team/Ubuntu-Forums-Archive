---
title: "Moto4lin is driving me"
date: 2010-03-06
forum: General Help
---

### Post by pmfabri on 2010-03-06
I have installed moto4lin, as I want to be able to get pictures off my razr v3mM, which I could easily do in Windows. I found a guide for connecting a v3m, but for some reason moto4lin is screwing around with me. Here is my log:


[info] Phone is unpluged. Please connect it
[info] Phone pluged as AT
[info] Switching device /dev/ttyACM0 to P2K mode...
[error] Unable to open device
[error] Please check preferences
[info] Switching device /dev/ttyACM0 to P2K mode...
[error] Unable to open device
[error] Please check preferences
[info] Switching device /dev/ttyACM0 to P2K mode...
[error] Unable to open device
[error] Please check preferences
[info] Switching device /dev/ttyACM0 to P2K mode...
[error] Unable to open device
[error] Please check preferences
[info] Switching device /dev/ttyACM0 to P2K mode...
[error] Unable to open device
[error] Please check preferences
[info] Switching device /dev/ttyACM0 to P2K mode...
[error] Unable to open device
[error] Please check preferences
[info] Switching device /dev/ttyACM0 to P2K mode...
[error] Unable to open device
[error] Please check preferences
[info] Switching device /dev/ttyACM0 to P2K mode...
[error] Unable to open device
[error] Please check preferences
[info] Phone is unpluged
[info] Phone pluged as P2K
[info] Phone pluged as AT
[info] Switching device /dev/ttyACM0 to P2K mode...
[error] Unable to open device
[error] Please check preferences
[info] Phone is unpluged
[info] Phone pluged as P2K
[info] Phone pluged as AT
Getting file list
[error] Unable to get drive list
Complete
Try to connect
[info] AT phone found
[info] Switching device /dev/ttyACM0 to P2K mode...
[error] Unable to open device
[error] Please check preferences
[error] Unable to connect
[info] Phone is unpluged
[info] Phone pluged as P2K
[info] Phone pluged as AT
[info] Switching device /dev/ttyACM0 to P2K mode...
[error] Unable to open device
[error] Please check preferences
[info] Switching device /dev/ttyACM0 to P2K mode...
[error] Unable to open device
[error] Please check preferences
[info] Switching device /dev/ttyACM0 to P2K mode...
[error] Unable to open device
[error] Please check preferences
[info] Switching device /dev/ttyACM0 to P2K mode...
[error] Unable to open device
[error] Please check preferences
[info] Switching device /dev/ttyACM0 to P2K mode...
[error] Unable to open device
[error] Please check preferences
[info] Switching device /dev/ttyACM0 to P2K mode...
[error] Unable to open device
[error] Please check preferences
[info] Switching device /dev/ttyACM0 to P2K mode...
[error] Unable to open device
[error] Please check preferences
[info] Switching device /dev/ttyACM0 to P2K mode...
[error] Unable to open device
[error] Please check preferences
Reading seem 0032_0001.seem
[error] Unable to read seem
Reading seem 0032_0001.seem
[error] Unable to read seem
[info] Phone is unpluged
[info] Phone pluged as P2K
[info] Phone pluged as AT
Try to connect
[info] AT phone found
[info] Switching device /dev/ttyACM0 to P2K mode...
[error] Unable to open device
[error] Please check preferences
[error] Unable to connect
[info] Switching device /dev/ttyACM0 to P2K mode...
[error] Unable to open device
[error] Please check preferences
[info] Switching device /dev/ttyACM0 to P2K mode...
[error] Unable to open device
[error] Please check preferences
[info] Switching device /dev/ttyACM0 to P2K mode...
[error] Unable to open device
[error] Please check preferences
[info] Switching device /dev/ttyACM0 to P2K mode...
[error] Unable to open device
[error] Please check preferences
[info] Switching device /dev/ttyACM0 to P2K mode...
[error] Unable to open device
[error] Please check preferences
[info] Switching device /dev/ttyACM0 to P2K mode...
[error] Unable to open device
[error] Please check preferences
Try to connect
[info] AT phone found
[info] Switching device /dev/ttyACM0 to P2K mode...
[error] Unable to open device
[error] Please check preferences
[error] Unable to connect

---

### Post by Fir3chi3f on 2010-03-06
Do you have a SD card in your razr? I had a v3xx a while back and I remember the SD card automatically mounting and working as a modem in ubuntu without additional software.

I do remember trying to install moto4lin or something like that, but never could get it to work.

---

### Post by pmfabri on 2010-03-07
There is no SD card in my v3m

---

### Post by pmfabri on 2010-03-07
Bump:D

---

### Post by darolu on 2010-03-07
I use the same phone, this is how I solve it every time I install it. Run it with sudo:
```
$ sudo moto4lin
```
It should work fine now, change the AT to P2K settings and next time try runnign with your regular user and should work fine.

---

### Post by srvfan01 on 2011-03-09
> **darolu said:**
> I use the same phone, this is how I solve it every time I install it. Run it with sudo:
```
$ sudo moto4lin
```It should work fine now, change the AT to P2K settings and next time try runnign with your regular user and should work fine.


[SIZE=2][FONT=Comic Sans MS]**I have a motorola razr v3 and have installed moto4lin but it won't let me switch from AT mode to P2K mode... any thoughts?:confused:**[/FONT][/SIZE]

---

### Post by mrford121 on 2012-12-13
I found an old v3m today and decided to start playing around with it.  I have been looking all over and have found numurous posts about problems with this phone and using bitpim and moto4lin.  I figured I should share what I have found out since there havnt been any good resolutions to this and it has been a few years.  I have managed to get a little further than most of what I have read but still am not fully functional.  First off,  I found that moto4lin has some interested quirks about keeping the settings.  If you want the settings to take you have to run moto4lin as a user and enter the settings for your phone.  After that run sudo moto4lin and the settings made will be there like they should.  Took me a long time of having the settings reset on me to figure that out.   The settings I used for my phone to get it to connect was 

> 
ACM Device: /dev/ttyUSB0 
AT Vendor ID: 22b8
AT Product ID: 2a64
P2K Vendor ID: 22b8
P2K Product ID: 2a61
now comes the problem.  

> 
[info] Phone connected as P2K
[error] Unable to get phone model
Getting file list
[info] Found drives: [ ]
[info] Search request: [/|*]
[info] Found 154 files
Complete
Reading seem 0032_0001.seem
[error] Unable to read seemI cannot access the seem on the phone.  This has kind of left me at a dead end so I decided to try using bitpim. Since I have not altered my permissions I have to run this with sudo otherwise nothing will work on it.  After starting up bitpim I am prompted with a message telling me that 

> Other CDMA phone on /dev/ttyUSB1 - DetectedThis default setting will allow me to browse and save files off of the phone.  I have not tried altering or saving to the phone yet.  The problem starts again when I try to pull the phonebook off the phone.  When I click on the get phone data button on the top left I am not allowed to select anything at all. So I go into the settings and name the device as a V3m.  Now I can select a couple of things to download from the phone but trying it results in 
> Moto-V3m on /dev/ttyUSB1: The phone is not responding while transitioning mode from none to phonebook.Even though bitpim automatically detected my phone on USB1 I have to go in and change the settings to connect through USB0.  Earlier attempts at this allowed me to download ringtones and media from the phone but not phonebook or sms.  I have tried using the V3cm phone setting and it still is no change from this.  I would like to be able to edit the seem file but am about to call it a day on this.  Any new input would be appreciated.

---


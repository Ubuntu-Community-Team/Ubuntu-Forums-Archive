---
title: "Hauppauge 950Q in karmic"
date: 2009-11-02
forum: General Help
---

### Post by gotmonkey on 2009-11-02
Does anyone know how to get a Hauppauge 950Q USB tv tuner working in 9.10? I have been trying for a couple of days now to get it working and have not had any luck. 

Thanks

---

### Post by iaguy2 on 2009-11-20
I'm not able to get mine going either.  I upgraded from Jaunty before I bought this 950Q.  The device seems to be loaded but it can't see anything. Mythtv doesn't find anything on channel scans.  Tvtime just shows a blank screen.  I'm connected to digital cable.  Here is my dmesg:
 4230.376721] DVB: adapter 0 frontend 0 frequency 863000000 out of range (54000000..858000000)
[ 4230.398089] DVB: adapter 0 frontend 0 frequency 869000000 out of range (54000000..858000000)
[ 4230.400522] DVB: adapter 0 frontend 0 frequency 875000000 out of range (54000000..858000000)
[ 4230.401308] DVB: adapter 0 frontend 0 frequency 881000000 out of range (54000000..858000000)
[ 4230.403196] DVB: adapter 0 frontend 0 frequency 887000000 out of range (54000000..858000000)
[ 4281.396072] phy0: frequency change failed
[ 4401.393394] phy0: frequency change failed
[ 4452.225023] xc5000: waiting for firmware upload (dvb-fe-xc5000-1.6.114.fw)...
[ 4452.225039] usb 1-2: firmware: requesting dvb-fe-xc5000-1.6.114.fw
[ 4452.252377] xc5000: firmware read 12401 bytes.
[ 4452.252382] xc5000: firmware uploading...
[ 4464.524065] xc5000: firmware upload complete...

---

### Post by mjharold on 2009-11-21
I have the 950Q, it did not work in 9.04, but I upgraded to 9.10, and plugged in and works.  I will tell you it is tricky to get it to start scanning.  I believe I had all settings set and had to exit Kaffine and back into Kaffine to get it to scan.  can only get it to scan and work in Kaffine.  After changing a few channels you have to exit and re-enter Kaffine, it gets "lost".  I am new to Linux/Ubnutu

---

### Post by Victormd on 2009-12-16
This card works out of the box in Karmic (I believe it was already supported in earlier versions). I have it setup in MythTV and it works great - only problem is that it only works with over-the-air - I couldn't get it to work connected to the cable... I have it setup as a DVB card in Myth backend setup and it scans the channels and finds about 20 OTA channels...

---

### Post by slick666 on 2009-12-16
I've had a 950Q since 8.10 and it works fine for me. Back in some older versions of ubuntu I had to download the firmware and copy it into the /lib/firmware folder. I think from 9.04 it's worked out of the box for me. If someone is having problems with getting it to work please start a thread or point to one that is still unsolved.

---

### Post by ttorion on 2010-01-22
Definitely doesn't work out of the box as PnP for me. I just installed a vanilla 9.10 (was running fedora), plugged in the card and dmesg keeps on saying I2C fails with no good reason. I've tried this card on multiple laptops- none work, so my conclusion is it's a no-go. (card works under windows)

Yeah- the xc5000 firmware file is included with 9.10, but doesn't load, and I don't get much useful feedback from dmesg.

I've tried installing both different firmwares in two different locations (just in case...), updating V4L. No go. If it works for you, please share how you got it to work

---

### Post by gotmonkey on 2010-01-23
I have tvtime installed and I get video, but no audio output. I can see the sound level meter registering audio, but I am getting nothing out of the speakers.

---


---
title: "What to find the name of my sound driver ?"
date: 2011-12-08
forum: General Help
---

### Post by tarundas on 2011-12-08
I want to know the name of sound driver I have. Ubuntu 11.10 ...help please

---

### Post by mastablasta on 2011-12-08
you sound driver is ALSA.
 
You probabbly mean how to find your sound card? it should be in the sound settings.
 
if it's now then open the reminal and type: 
 
lspci 
 
this command will show everyhting connected to motherboard via PCI or if it's an onboard device.
copy and post the output here.
 
 
another ocmmand to give you hardware info is 
 
lshw
 
this one lists all hardware and should include the sound card/chip.

---

### Post by tarundas on 2011-12-08
Thank you for your reply ... I did something wrong and deleted something and now I neither have volume control icon nor any devices in sound window ... I had two of them  ... 1. VT something 2.Logitech USB Headset. My stereo is hooked  with my PC and I used to switchover between devices according to use ... listening to music or talking with someone on IM ... I was trying following link to fix it. It says something about Audio Driver other than ALSA like "via82xx"
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

BTW ... I am having no problem listening music ...it's working but I can't switchover to my headset or control the volume in my pc

---

### Post by mastablasta on 2011-12-08
you could try removing / purging alsa packages and then reinstalling them. ALSA are linux sound drivers.

---

### Post by tarundas on 2011-12-08
> **mastablasta said:**
> you could try removing / purging alsa packages and then reinstalling them. ALSA are linux sound drivers.

Ok, I installed Pulse audio and my devices are back, now I want my volume control icon back it's not there in task bar

---

### Post by tarundas on 2011-12-08
Well, I got the command from another thread in this forum. my Volume control is back now 

```
sudo apt-get install indicator-sound
killall unity-panel-service
```

Thank you

---


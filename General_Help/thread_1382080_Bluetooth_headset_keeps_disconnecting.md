---
title: "Bluetooth headset keeps disconnecting"
date: 2010-01-15
forum: General Help
---

### Post by StormHorse on 2010-01-15
Ok, short version:  My bluetooth headset keeps disconnecting.

Full version:

I'm using a 64-bit distro of 9.10 on a 1.6 GHz AMD Turion 64 laptop, with an external bluetooth dongle and a bluetooth headset.  The dongle is recognized right off, the headset pairs perfectly through the bluetooth preferences panel, and sound redirects through the sound preferences panel...  For about 2 minutes.  I know, it's odd, but every 2 minutes or so bluetooth disconnects from the headset.  Sound shifts to the speakers, the applications don't miss a beat, and when I reconnect the headset through the bluetooth control it shifts right back to the headset.  This happens regardless of other programs running.  I tried it with no other applications running, and with a fairly heavy load, and it reoccurs.

Here's the odd part:  I had the CPU set on "Ondemand," to save battery power, but when I plugged in and shifted it to "Performance," it started happening ever 4 minutes or so...

I've Googled around and found plenty about getting my headset to connect, but nothing about KEEPING it connected.

Thoughts?

As an aside, I want to comment on how well the sound seems to work on this distro, and to thank all the contributors who've helped make it that way.

---

### Post by gradinaruvasile on 2010-01-15
Try using blueman instead of the default bluetooth manager.

---

### Post by khhc0623 on 2010-02-11
I get the same problem with my bluetooth headset. It keeps disconnecting every 2 minutes or so. I've set up blueman in my Ubuntu 9.10, and my bluetooth headset has paired successfully in blueman. Does anyone have updates on solving the issue?

---

### Post by jr.swordfish on 2010-06-12
[SIZE=4]Bluetooth disconnects after few seconds (especially trying to use jawbone with skype) with the default bluetooth manager. 

[/SIZE]

---

### Post by Arka79 on 2010-11-01
Hi, have the same issue. Recently replaced default Ubuntu bluetooth manager with blueman, but problem persists: my headset disconnects during the skype call (with Sound Test Service also).

After disconnect open bluetooth devices and click on my headset (plantronics discovery) and then -> Refresh Services.
Manager shows error: Host is down.

---

### Post by z662 on 2010-11-21
bump

---

### Post by pzukowski on 2011-01-18
Has this been resolved?  I have the same issue on several machines, with different bluetooth hardware.  It manifests itself as the headset going dead in the middle of a call (skype or google voice) and the sound gets switeched to the default pulseaudio speaker/mic.  This is very annoying and Blueman does not help!  Please help someone!

---

### Post by jr.swordfish on 2011-06-05
Disable/uncheck "Allow Skype to automatically adjust my mixer levels" in Skype->Options->Sound Devices. This has solved the auto disconnect of bluetooth headset when using with Skype with my setup.

---

### Post by rajun198 on 2011-11-06
hey :(
I have the same problem too.

i use ubuntu 11.04 in a dell inspiron 1525(built in bluetooth) and Nokia BH-503 Headset

headset shows connected but no audio after 2 minutes (if the device is kept silent for 2 minutes). Any solutions will be appreciated 

Thanks in advance

---


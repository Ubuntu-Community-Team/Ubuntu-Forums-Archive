---
title: "bluetooth adapter not working (Cambridge Silicon Radio)"
date: 2010-11-22
forum: General Help
---

### Post by gandaran on 2010-11-22
> Bus 002 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
I bought this cheap bluetooth adapter on ebay, it doesn't work maybe it needs drivers, do you know how can I fix it.

---

### Post by gandaran on 2010-11-22
got it working now, 2 hours to get it working! it took me 2 minutes to do the same in windows xp, I just don't know why bluetooth is so difficult in linux/ubuntu.

---

### Post by hkphooey on 2010-11-22
So what did you do to fix it? Just going through the same pain myself. 

Basically when I try to pair the adapter with my phone, it sends the wrong passcode. The one that appears on my phone is different to the one ubuntu displays, and I have no opportunity to manually type it in on my phone. 

Same adapter. Phone is a Samsung Champ. Running Ubuntu 10.04 or 10.10. I've tried the adapter with three different computers, and using blueman and the standard gnome bluetooth setup. My previous adapter works fine with all three computers. 

So clearly something is wrong with this particular adapter.

---

### Post by gandaran on 2010-11-23
> **hkphooey said:**
> So what did you do to fix it? Just going through the same pain myself. 

Basically when I try to pair the adapter with my phone, it sends the wrong passcode. The one that appears on my phone is different to the one ubuntu displays, and I have no opportunity to manually type it in on my phone. 

Same adapter. Phone is a Samsung Champ. Running Ubuntu 10.04 or 10.10. I've tried the adapter with three different computers, and using blueman and the standard gnome bluetooth setup. My previous adapter works fine with all three computers. 

So clearly something is wrong with this particular adapter.
no I haven't fixed anything yet, its still not working properly, the initial problem was enabling bluetooth, the adapter works 1 out of 10 times when I insert it but when it doesn't I just cant enable bluetooth with the standard gnome bluetooth so I have installed blueman, with blueman I can enable bluetooth and connect to bluetooth device but what I want is the adapter to work strait away every-time when I insert it, maybe the problem is with the adapter or some bug, I will search launchpad bugs when I have time and try to fix this.

---

### Post by hkphooey on 2010-11-23
Ah, shame, sounds like a very different problem to mine. 

It may not be just bluetooth though. With every bluetooth dongle I've had, Ubuntu hasn't responded too well to unplugging it and replugging it. I usually have to reboot to 'reset' bluetooth and then it works again. Logging out and in again doesn't work. I believe this might be something to do with the way gnome works with dbus and udev, but I really don't know enough about that stuff. 

So I'd say just grit your teeth, reboot, commit yourself to a 1 minute wait, and you'll be fine.

---

### Post by gandaran on 2010-11-23
I think I have found the fix here for my problem 
[https://bugs.launchpad.net/blueman/+bug/496733](https://bugs.launchpad.net/blueman/+bug/496733)
looks like it is working now (I'm still testing), if I switch on the bluetooth device and plug in the adapter bluetooth works strait away now, no need to enable/start anything and I have removed blueman theres no need for it now, this is exactly how I wanted it to work.

---


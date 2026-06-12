---
title: "Bluetooth?"
date: 2009-06-27
forum: General Help
---

### Post by ManDay on 2009-06-27
Hi, currently typing on a mobilephone, so keeping it short... I tried to pair this phone via bluetooth, but without success. The amoumt of configuration in the out-of-the-box (gnome?-) bluetooth software is pathetic, too - so I dont really wonder that it doesnt work. Can you recomment a _well working_ bluetooth pkg from the repos? Thanks

---

### Post by Hobgoblin on 2009-06-27
Not in the repos but [Blueman](http://blueman-project.org/) might be what you are looking for, you can add their own [repo](https://edge.launchpad.net/~blueman/+archive/ppa) to make life easy.

---

### Post by khelben1979 on 2009-06-27
Install [BlueZ]("http://en.wikipedia.org/wiki/Bluez#BlueZ").

```
sudo apt-get install bluez
```

---

### Post by Hobgoblin on 2009-06-27
> **khelben1979 said:**
> Install [BlueZ]("http://en.wikipedia.org/wiki/Bluez#BlueZ").

```
sudo apt-get install bluez
```

That's installed as default and has been for some versions of Ubuntu.

---

### Post by ManDay on 2009-06-27
Hi, its indeed Bluez that I ve been trying to use. I try

hcitools cc ...

and shortly (2 seconds) after I thereby connected, the  connection disappears. Any clue?

---

### Post by ManDay on 2009-06-27
I managed to get a PPP conection up but eventually it doesnt work because the damn bluetooth link just vanishes a few seconds after it has been established. Another bug in H/W or software? Please help!

---

### Post by Hobgoblin on 2009-06-27
Ah, it's bluetooth dialup you are trying to get working.

[these instructions](https://help.ubuntu.com/community/BluetoothDialup) will get you going with the standard packages.  You'll need to tell Firefox to work online though because it will think there is no internet connection.  You can use gnome-ppp to establish the connection once /dev/rfcomm0 is set up.

But Blueman makes it much easier, with a couple of clicks and integration with network manager (hence Firefox and other apps will work as intended).

---

### Post by ManDay on 2009-06-27
Hi, 'these instructions' are unassissable for me (still browsing on my phone, a pain in the ***, Im telling you). As I stated, the main problem for me is that the bluetooth link disengages immediately after I established it (unless  I use gnome Bluez, by the way, which is just shitty useless, however, as it renders not to be capable of anything besides file transfer, which doesnt work anyway). Hence, these tutorials dont help me much, as they assume a holding link.

---

### Post by Hobgoblin on 2009-06-27
Do you have a USB cable for the phone?

The way I did it was to put my phone (a nokia N95) into PC Suite mode, connect the USB cable, follow the on screen prompts.  This gave me a working internet connection in order to follow the instructions.

---

### Post by ManDay on 2009-06-27
Hell! I made! Screw Bluez and the Gnome Network-Manager that useless junk - didn't work one bit, but I made it nonetheless!

Eventually, I'm not quite sure what was the issue, but I suppose I just had to get the pppd "chatscript" right, it just didn't suit my Provider.

So, for anyone coming across this topic, being as frustrated as I've been and looking for a way to get it going, here is how I did it.

With help of [https://help.ubuntu.com/community/BluetoothDialup](https://help.ubuntu.com/community/BluetoothDialup)

1.) Set up the rfcomm configuration file as described.
2.) Fire up rfcomm to connect to the mobile phone (yields a stable link, other than the stupidd hcitool!) "rfcomm connect rfcomm0"
3.) Set up /etc/ppp/peers/... and /etc/chatscripts/... and (what was the clue in my case) make sure you have the correct settings in ./chatscripts/...!
4.) Run pon ...

voila!

Thanks to all! I'm going to shoot Bluez and all this ******** right to the moon!


...Oh dearest keyboard, how good it feels to have you back... You don't know what you've gone, until it's gone, always remember lads! :P

---


---
title: "Need to test a wireless adapter"
date: 2012-07-07
forum: General Help
---

### Post by Mazate on 2012-07-07
Howdy

I need to test a wireless adapter I received today for use on my desktop.  I need to replace the motherboard in it so the only other thing I have to test the adapter on is a laptop.  Is there a way to disable the built-in wireless adapter in my laptop so that it will automatically revert to the usb adapter I'll be testing on it?

Thanks!

---

### Post by carl4926 on 2012-07-08
If I add a USB wireless device to my laptop I can toggle to use it in the NM.

You could also blacklist your built in device or remove the driver temp for a session.

---

### Post by gandaran on 2012-07-08
> **Mazate said:**
> Howdy

I need to test a wireless adapter I received today for use on my desktop.  I need to replace the motherboard in it so the only other thing I have to test the adapter on is a laptop.  Is there a way to disable the built-in wireless adapter in my laptop so that it will automatically revert to the usb adapter I'll be testing on it?

Thanks!
your laptop should have a switch or another way to disable wireless on the keyboard but even with both wireless devices enabled if the external adapter is supported you can choose on the panel network manager icon which one to use.

---

### Post by Mazate on 2012-07-08
> **gandaran said:**
> your laptop should have a switch or another way to disable wireless on the keyboard but even with both wireless devices enabled if the external adapter is supported you can choose on the panel network manager icon which one to use.

"If the external adapter is supported" is the key phrase.  I can't find any wireless adapters that are supported.  Until I do, my desktop is just a paper weight.

---

### Post by gandaran on 2012-07-08
> **Mazate said:**
> "If the external adapter is supported" is the key phrase.  I can't find any wireless adapters that are supported.  Until I do, my desktop is just a paper weight.
let us know which brand and model of the adapter
plug in the adapter and type in terminal
```
lsusb
```
the best wireless chip brands that work out of the box are Atheros, Ralink and Realtek brands but if it doesn't work out of the box you can always install the driver in most cases.

---

### Post by carl4926 on 2012-07-08
[http://www.amazon.co.uk/tenda-wireless-n150-usb-adapter-%C2%A37-99/s?ie=UTF8&keywords=Tenda%20Wireless-N150%20USB%20Adapter%20%C2%A37.99&rh=i%3Aaps%2Ck%3ATenda%20Wireless-N150%20USB%20Adapter%20%C2%A37.99&page=1](http://www.amazon.co.uk/tenda-wireless-n150-usb-adapter-%C2%A37-99/s?ie=UTF8&keywords=Tenda%20Wireless-N150%20USB%20Adapter%20%C2%A37.99&rh=i%3Aaps%2Ck%3ATenda%20Wireless-N150%20USB%20Adapter%20%C2%A37.99&page=1)

These work so well it's almost unbelievable

---

### Post by Mazate on 2012-07-08
> **gandaran said:**
> let us know which brand and model of the adapter
plug in the adapter and type in terminal
```
lsusb
```the best wireless chip brands that work out of the box are Atheros, Ralink and Realtek brands but if it doesn't work out of the box you can always install the driver in most cases.

Ok, here it is.

---

### Post by gandaran on 2012-07-08
which ubuntu version do you have?
if not 12.04 try updating, maybe the Ralink chip RT5370 will work out of the box now, if not try following this thread to install the driver for your adapter
[http://ubuntuforums.org/showthread.php?t=1800178](http://ubuntuforums.org/showthread.php?t=1800178)
[http://ubuntuforums.org/showthread.php?t=1987908](http://ubuntuforums.org/showthread.php?t=1987908)
[https://help.ubuntu.com/community/WifiDocs/Device/Tenda_W311M](https://help.ubuntu.com/community/WifiDocs/Device/Tenda_W311M)

---


---
title: "Having problems with Linksys WUSB54Gv2"
date: 2009-07-28
forum: General Help
---

### Post by TheReaper0218 on 2009-07-28
Hey I'm new to Ubuntu and I'm trying to install my linksys to my PC because I have two computers in my house, one with windows XP that has a WI FI box and mine which has Ubuntu Jaunty 9.04 and only a Linksys receiver. Now I have my computer hooked up to the internet in the other room via eathernet cable right now and I installed Wine and installed the drivers for the Linksys that way and Ubuntu says they're installed but how do I get my WUSB54Gv2 to connect to the WIFI now? 
P.S I have heard of ndiswrapper I just cannot get it to install all of the "totorials" really sucked.

---

### Post by philcamlin on 2009-07-28
you have 2 dfferent devices you said in there so wich one is it :popcorn:
54 or 52 :P

---

### Post by TheReaper0218 on 2009-07-28
Lol sorry I meant 54 X]

---

### Post by speedwell68 on 2009-07-28
> **TheReaper0218 said:**
> Hey I'm new to Ubuntu and I'm trying to install my linksys to my PC because I have two computers in my house, one with windows XP that has a WI FI box and mine which has Ubuntu Jaunty 9.04 and only a Linksys receiver. Now I have my computer hooked up to the internet in the other room via eathernet cable right now and I installed Wine and installed the drivers for the Linksys that way and Ubuntu says they're installed but how do I get my WUSB54Gv2 to connect now? 
P.S I have heard of ndiswrapper I just cannot get it to install all of the "totorials" really sucked.

I have one of those and it worked out of the box, without all that wine and ndiswrapper stuff.  Mine came supplied with a USB extension lead and it didn't work when plugged into that.  When I plugged the dongle directly into the USB socket on my PC it worked first time.

---

### Post by TheReaper0218 on 2009-07-28
I have the WUSB54Gv2 plugged in to the computer with the USB cable. What I mean is how do I get it to connect to the WIFI on the other computer?

---

### Post by speedwell68 on 2009-07-28
> **TheReaper0218 said:**
> I have the WUSB54Gv2 plugged in to the computer with the USB cable What I mean is how do I get it to connect to the WIFI on the other computer?

If you click on the 'network manager' icon in the gnome tray is there a list of available wireless networks?  If not remove the USB extension lead and plug the dongle into the USB port directly.

---

### Post by TheReaper0218 on 2009-07-28
Yeah that's what's getting me there's no list of any wireless networks to connect to. How do I connect it directly?

---

### Post by speedwell68 on 2009-07-28
> **TheReaper0218 said:**
> Yeah that's what's getting me there's no list of any wireless networks to connect to. How do I connect it directly?

As far as I know you can't.  Have you disconnected it from the USB extension and plugged it in direct?  If you have and still have no joy, reboot with it plugged in to the USB socket and check that list again.  If you still have no joy then run this command from the terminal...

```
lsusb
```

...then post the output here.

---


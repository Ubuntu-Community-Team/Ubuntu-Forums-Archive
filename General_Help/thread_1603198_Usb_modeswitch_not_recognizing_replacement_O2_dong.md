---
title: "Usb_modeswitch not recognizing replacement O2 dongle"
date: 2010-10-22
forum: General Help
---

### Post by StuartN on 2010-10-22
I had a Huawei e1752c O2 Mobile Broadband dongle working fine in Ubuntu 9.04 using usb_modeswitch, with settings taken from [http://www.stroobant.be/huawei-e1752-mobiel-internet-op-linux-ubuntudebian](http://www.stroobant.be/huawei-e1752-mobiel-internet-op-linux-ubuntudebian)

After renewing an annual O2 contract, I have a new e1752c and it does not work in Ubuntu 9.04, even after installing the latest usb_modeswitch package and data. The new dongle does work perfectly on an identical laptop that has Ubuntu 10.04 with a freshly installed Network Manager and usb_modeswitch.

I am guessing that there is a rule (udev or whatever) hanging over from somewhere that needs deleting, but I don't know where to look, and don't see any useful error messages - the device lists as Vendor 12d1, Product 1446 before and after usb_modeswitch runs, but becomes Product 140c in the Ubuntu 10.04 system.

Please help me get this working.

---

### Post by Hippytaff on 2010-10-22
Don't fancy upgrading to 10.04? :-)

---

### Post by StuartN on 2010-10-22
> **Hippytaff said:**
> Don't fancy upgrading to 10.04? :-)

Well yes, but the dongle is on my daughter's 9.04 and she is visiting. If I was sure that I could return it fully functional, with all her packages, data and profiles, then I would.

So in the meantime, anything identifying the reason for the device not switching mode would really, really be appreciated.

---

### Post by Hippytaff on 2010-10-22
Run it from the 10.04 live cd maybe?

---

### Post by StuartN on 2010-10-22
> **Hippytaff said:**
> Run it from the 10.04 live cd maybe?

She brought it home from university and wants to take it back with her broadband working! I think I have it - and it is picking up the mobile broadband after a reboot, so it should have stuck:

I recreated her accesspoint details in nm-applet and I commented out a line referring to the same device in /lib/udev/rules.d/61-option-modem-modeswitch.rules:

```
#ATTRS{idVendor}=="12d1", ATTRS{idProduct}=="1446", RUN+="modem-modeswitch -v 0x%s{idVendor} -p 0x%s{idProduct} -t option-zerocd"
```

---

### Post by Hippytaff on 2010-10-22
if you want to test it to make sure I guess you could install it as a small partition and test. If it works ok then install it on the whole disc (assuming 9.04 is on the whole drive) or if it doesn't work get rid if it doesn't?

just a thought :-)

---


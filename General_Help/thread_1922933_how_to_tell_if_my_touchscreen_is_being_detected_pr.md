---
title: "how to tell if my touchscreen is being detected properly"
date: 2012-02-09
forum: General Help
---

### Post by HybriDPjT on 2012-02-09
hey all!

pretty much as the title says..
ive got myself an AOC e2239fwt monitor and so far the single touch seems to work ok but not the multitouch.

im running ubuntu 11.04 x64

info that may help?
well as im using an nvidia card, i have the nvidia drivers installed, and the nvidia settings reports back the correct monitor name (2239)

but according to monitors in the control center its unknown.
and if i do ***xinput list*** from a terminal it reports a ***quanta optical touch screen***?

im connecting through hdmi and ive double checked the usb cable is connected too.

i can confirm that the multi touch works in win 7.

can anyone help? is there any drivers out there i should be using or software i need to install?
(speaking of which i have utouch installed)

thanks in advance!

---

### Post by mightybuddha on 2012-02-16
Hi,

What is the output of 

```
lsusb
```

I haven't had much luck with multitouch in the past, though your best bet is probably the drivers at enac.

[http://lii-enac.fr/en/architecture/linux-input/multitouch-ubuntu-howto.html](http://lii-enac.fr/en/architecture/linux-input/multitouch-ubuntu-howto.html)

If the 8 digit ID for your touchscreen (found through lsusb, eg. 0596:0500) is in this list then you should be in luck :)

[http://lii-enac.fr/en/architecture/linux-input/multitouch-devices.html](http://lii-enac.fr/en/architecture/linux-input/multitouch-devices.html)

---


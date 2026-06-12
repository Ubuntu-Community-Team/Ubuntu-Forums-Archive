---
title: "Things aren't working right."
date: 2011-01-04
forum: General Help
---

### Post by nibiru8722 on 2011-01-04
So I have a few problems.
Finally got Ubuntu installed on my external.
When it boots up, it's great.
WHEN it boots up.
Half the time my computer doesn't recognize that my external is plugged in. How do I fix this? I've tried every USB port but it seems to be hit or miss every time.

And now my wireless doesn't work. I have an Asus WL-138G V2 Wireless Card, and I've tried ndiswrapper (or whatever that program's called), I've tried dozens of different things, NOTHING IS WORKING. How do I get this driver to function!?

---

### Post by Bucky Ball on 2011-01-04
Plug in an ethernet cable and get online if you haven't already. This might fix the wireless problem by offering you appropriate drivers and firmware.

Check in System->Administration->Additional Drivers. What there?

---

### Post by nibiru8722 on 2011-01-04
When I checked while offline, nothing was there, even after I installed countless things.
Now I can't even get my USB to boot. It doesn't show up anymore.

---

### Post by BicyclerBoy on 2011-01-04
The wireless device needs a driver & proprietary firmware.
This means adding restricted repos to synaptic packager manager.

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

ndiswrapper tries to allow use of a windows driver..

A native driver must be available now..

Need to be sure what the hardware is 
lspci

What *buntu version ?
What is the PC h/w generally?

Hard to blame *buntu for not detecting/booting external HD more likely your PC BIOS or BIOS boot device setup or ext HDD device.

---

### Post by Bucky Ball on 2011-01-04
Try and avoid ndiswrapper. It sucks (mostly) and is superseded for most cards now.

System->Administration->Synaptic Package Manager->search for 'ubuntu-restricted-extras'. Don't really need a guide.

The issue with this is you need to be online to install the package.

---

### Post by nibiru8722 on 2011-01-05
> **Bucky Ball said:**
> Try and avoid ndiswrapper. It sucks (mostly) and is superseded for most cards now.

System->Administration->Synaptic Package Manager->search for 'ubuntu-restricted-extras'. Don't really need a guide.

The issue with this is you need to be online to install the package.

I got my desktop hooked up with a wired connection, and tried this, and it still isn't letting me set up a wireless connection. I can see that the drivers are installed but they aren't doing anything.

---

### Post by Bucky Ball on 2011-01-05
Could you open a terminal (Applications->Accessories->Terminal) and paste these two commands one at a time:

```
iwconfig
ifconfig
```Hit return after each and post the output of both commands. :)

---


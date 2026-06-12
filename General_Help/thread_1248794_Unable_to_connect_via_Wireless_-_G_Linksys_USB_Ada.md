---
title: "Unable to connect via Wireless - G Linksys USB Adapter! Please help!"
date: 2009-08-24
forum: General Help
---

### Post by Lavaeagle on 2009-08-24
My situation:
Ubuntu 9.04
Compaq F700
Linksys Compact Wireless-G USB Adapter - WUSB54GC

Connecting to a Linksys router.
Am able to connect via ethernet. 
I cannot however get the drivers to work for the adapter.  So wireless internet is just a dream for me. 

Any ideas? Commands? Tutorials?

Thank you!

---

### Post by miwaypet on 2009-08-24
For my little guide to work you need the .inf file for your wireless driver.

First we will remove any wireless driver installed

```
$ sudo ndiswrapper -r (your driver here)
```

That removes the driver(s)

Install the driver

```
$ sudo ndiswrapper -i ./(your driver here).inf
```

(should say something to the effect of installing driver)

```
$ sudo modprobe -r ndiswrapper
```

```
$ sudo modprobe ndiswrapper
```

```
$ sudo ndiswrapper -m
```

```
$ sudo ndiswrapper -l 
```

(driver installed; hardware present.)

```
$ sudo bash -c 'echo "ndiswrapper" >> /etc/modules'
```

Completely power down the machine. Start back up again. If you saw hardware present earlier you should now see your wireless network.

---


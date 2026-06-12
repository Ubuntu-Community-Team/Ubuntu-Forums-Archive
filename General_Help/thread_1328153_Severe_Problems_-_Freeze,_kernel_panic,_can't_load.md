---
title: "Severe Problems - Freeze, kernel panic, can't load wlan kernel module!"
date: 2009-11-16
forum: General Help
---

### Post by Beliar on 2009-11-16
Hello Community,
I'm using Linux since several years and Ubuntu is my main OS since 2 years,
but I never had such severe Problems like I have with Karmic, especially today!

Since last week, I have freezes and kernel panics and they seem to become more frequent. 
I tried to figure out the commonalities between the events and to look into the logs, but I can't come up with an explenation.

Today I had about 4 freezes/kernel panics in 2.5 hours, which is a new record. After rebooting, after the last one, my WLAN stopped working. ReLoading the ipw2200 Module would produce this message in dmesg:

```
[   11.946153] ipw2200: dmaWaitSync Failed
[   11.946722] ipw2200: Unable to load boot firmware: -1
[   11.946734] ipw2200: Unable to load firmware: -1
[   11.946740] ipw2200: failed to register network device
[   11.946805] ipw2200 0000:02:03.0: PCI INT A disabled
[   11.946820] ipw2200: probe of 0000:02:03.0 failed with error -5
```

My cable NIC seemed to make problems too (module skge). I rebooted and tried to unload + load the ipw2200 module. Didn't work. After the third try after the reboot, it suddenly worked. 
So I'm having freezes and kernel panics for no apparent reason (I was only Web-surfing and listening to music) and devices stop working and start working randomly.
I think I need some help :(

I have attached my latest kern.log. I would be very grateful, if someone had a look and maybe find out whats going on. If you need any other logs or information, just ask.

Thank you very much,
greets, Beliar

---

### Post by Kevbert on 2009-11-16
First thing to try would be a couple of runs of memtest86+ (from the boot menu). It may also be worth running
```
sudo apt-get install -f
```
in terminal (in case you have corrupted packages).

---

### Post by Beliar on 2009-11-16
Hello Kevbert,
thank you for your reply.

I let memtest86 run and it finished without errors.

apt-get reported no broken packages.

---


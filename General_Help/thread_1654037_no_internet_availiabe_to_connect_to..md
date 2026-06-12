---
title: "no internet availiabe to connect to."
date: 2010-12-27
forum: General Help
---

### Post by JackC64 on 2010-12-27
i just used wubi to install ubuntu 10.04 LTS. everything is smooth except i cant connect to internet. i get the wireless icon in the notification thing with a red exclamation point on it.
ive tried two different wireless connections, the important one being a verizon Mifi 2200 intelligent hotspot (its not usb-style, look it up). no matter what wifi i try, nothing shows up when i click the internet icon in the notification thing.

please help! ;)

---

### Post by JackC64 on 2010-12-28
can nobody help?

---

### Post by sdowney717 on 2010-12-28
[http://ubuntuforums.org/showthread.php?t=1171590](http://ubuntuforums.org/showthread.php?t=1171590)
it does work with ubuntu after it is activated using vz access manager in windows.
It should just be like hooking up to any wireless access point router

I wonder if it is a wubi issue. trouble shoot  this as wubi connecting to a wifi router.

---

### Post by sdowney717 on 2010-12-28
[http://ubuntuforums.org/showthread.php?t=1635913](http://ubuntuforums.org/showthread.php?t=1635913)

here is a windows killed my wubi wifi solved thread.


> So here is the skinny, in case the last link was left unread.
When you reboot, turn off your wifi switch. That's it, once you're all logged in - just turn it back on, and WALLA! You have network access...


---

### Post by JackC64 on 2010-12-28
> **sdowney717 said:**
> [http://ubuntuforums.org/showthread.php?t=1171590](http://ubuntuforums.org/showthread.php?t=1171590)
it does work with ubuntu after it is activated using vz access manager in windows.
It should just be like hooking up to any wireless access point router

I wonder if it is a wubi issue. trouble shoot  this as wubi connecting to a wifi router.
its been activated for a year... :/

---

### Post by Spyderkid on 2010-12-28
Could you un-plug and plug back in your device (if its a USB) and run 
```
lsusb
``` lsusb lists your USB devices plugged in. run [FONT="Courier New"]man lsusb[/FONT] if you want to find out more about what it does.



 for me please and post the output.

If its not a USB wireless adapter say so and don't run or post lsusb 

*thanks!*

---

### Post by JackC64 on 2010-12-29
its wireless.

---


---
title: "How to auto eject a CD?"
date: 2011-04-14
forum: General Help
---

### Post by pakennedy on 2011-04-14
I'm using a Three network broadband dongle for my net access at the moment. That's a ZTE MF-112.

It is obviously engineered for Windows and the procedure it goes through on a Windows box is to show up as a CD drive initially which then autoruns and checks for the presence of the drivers and installer software. Only after it has detected all that does it 'eject' the CD and bring the actual 3G device online.

This leads to a slight amount of... irritation. I tend to have a terminal window open anyway so typing */dev/cdrom1 eject* whenever I put the dongle in is no particular hardship, bu there must be some way to automate this.

The device turns up on */dev/cdrom1* and the 'disc' has the label '3 Connect'. 

Any suggestions on how to auto eject this thing whenever it shows up?

---

### Post by pakennedy on 2011-04-14
Ah.. looking into things further. It seems that udev may be my friend. Now I have a lot more study to do.

---

### Post by raziel09 on 2011-04-14
Which version of ubuntu are you using? I have exactly the same one and mine is found straight away in 10.10.


However in versions 9.10 - 10.04 i had the same issue; i used Usb-modeswitch (found this on google - someone here might be able to advise further as i'm only a casual user).

This then cured the issue - alternatively upgrade to the latest version
[B]
[/B]

---

### Post by Z.K. on 2011-04-15
> **pakennedy said:**
> I'm using a Three network broadband dongle for my net access at the moment. That's a ZTE MF-112.

It is obviously engineered for Windows and the procedure it goes through on a Windows box is to show up as a CD drive initially which then autoruns and checks for the presence of the drivers and installer software. Only after it has detected all that does it 'eject' the CD and bring the actual 3G device online.

This leads to a slight amount of... irritation. I tend to have a terminal window open anyway so typing */dev/cdrom1 eject* whenever I put the dongle in is no particular hardship, bu there must be some way to automate this.

The device turns up on */dev/cdrom1* and the 'disc' has the label '3 Connect'. 

Any suggestions on how to auto eject this thing whenever it shows up?


I had this problem with a Novatel USB760 and I had to use this udev rule:
```

SUBSYSTEM=="block", KERNEL=="sr[0-9]*", SUBSYSTEMS=="usb", ATTRS{idVendor}=="1410", ATTRS{idProduct}=="5030", PROGRAM="/usr/bin/eject $tempnode", OPTIONS+="last_rule"

```

I image it would work for you as well though you would have to change my device specific information with that of yours using udevadm info or lsusb -vvv.

---

### Post by linuxmaniack on 2011-04-16
go to places, then find your CD, DVD or blue ray drive. Right click on it, and click on eject

---

### Post by pakennedy on 2011-04-30
> **Z.K. said:**
> I
```

SUBSYSTEM=="block", KERNEL=="sr[0-9]*", SUBSYSTEMS=="usb", ATTRS{idVendor}=="1410", ATTRS{idProduct}=="5030", PROGRAM="/usr/bin/eject $tempnode", OPTIONS+="last_rule"

```I image it would work for you as well though you would have to change my device specific information with that of yours using udevadm info or lsusb -vvv.

That pretty much sorted it with the changes.... And now I'm on natty and the udev rule isn't needed any more because the thing just works anyway.

Thank you.

---


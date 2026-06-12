---
title: "Can not connect to the Internet via modem Aethra XB Starmodem"
date: 2010-12-27
forum: General Help
---

### Post by MaxDJs on 2010-12-27
Hello members,

I decided to retire from Microsoft Corporation, and I switched to Ubuntu 10.10. Now try to Establish a modem Aethra XB Starmodem using this [guide]("https://help.ubuntu.com/community/UsbAdslModem/ueagle-atm").

When I enter:

```
pon ueagle-atm
```

It throws me this error:

```
/usr/sbin/pppd: /usr/lib/pppd/2.4.5/ppoatm.so: cannot open shared object file: No such file or directory
/usr/sbin/pppd: Couldn't load plugin ppoatm.so

``` 


Could you advise me what to do?


Thank you for your answer

Sincerely,
MaxDJs

---

### Post by IWantFroyo on 2010-12-27
You were probably expected to have some programs or other code on the computer before you did that. Double check the guide.
Try System-Administration-Additional Drivers, if there's anything listed there on your modem, plug in an ethernet cable and download it.

---

### Post by MaxDJs on 2010-12-27
I can not download the drivers because I have another way to connect to the Internet

---

### Post by MaxDJs on 2010-12-27
I found a bug.

instead of pppoatm I wrote ppoatm.

When I run:

```
pon ueagle-atm
```

Terminal output:

```
Plugin pppoatm.so loaded.
PPPoATM plugin_init
PPPoATM setdevname_pppoatm - SUCCESS:8.48
```

But the internet still does not run.

It is intended that the firmware for the modem Aethra XB Starmodem?

BTW: Where can I download the latest version of Ubudsl for Ubuntu 10.10.?

Thanks

---


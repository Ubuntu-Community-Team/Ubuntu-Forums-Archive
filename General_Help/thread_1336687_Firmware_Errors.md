---
title: "Firmware Errors"
date: 2009-11-24
forum: General Help
---

### Post by barnaclebill18 on 2009-11-24
Hello,

Since clean installing 9.10 about a month ago, when starting the computer and when shutting down a black screen with white text flashes for a second or two, I can't figure out how to stop it so I can read it, with about 6 errors saying 'error firmware file xxxx' it goes so fast I can't read it.

It also says something about going to a website for drivers, but it is so fast, I just can't read it.

Tried to get a picture with the camera, not having much luck, but I did get one picture that some things can be read.

Everything I use seems to be working so I am just wondering what this means and is there a way to freeze the screen so I can read this better?

Thanks.

---

### Post by dcstar on 2009-11-24
> **barnaclebill18 said:**
> Hello,

Since clean installing 9.10 about a month ago, when starting the computer and when shutting down a black screen with white text flashes for a second or two, I can't figure out how to stop it so I can read it, with about 6 errors saying 'error firmware file xxxx' it goes so fast I can't read it.
........

It looks like something related to wireless LAN stuff, you can probably ignore it.

You can probably see the details in your Syslog file.

---

### Post by barnaclebill18 on 2009-11-24
Thanks for the quick reply.

I looked in the Syslog file and found this

```

   10.887035] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.887039] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.887042] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.887046] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.887050] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.804106] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   15.832079] b43 ssb0:0: firmware: requesting b43-open/ucode5.fw
[   15.837205] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   15.837281] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   15.837349] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[   15.839299] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   16.144088] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   16.151668] b43 ssb0:0: firmware: requesting b43-open/ucode5.fw
[   16.162563] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   16.162640] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   16.162708] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.

```

---

### Post by spamking2000 on 2009-12-01
Hello,

I'm having the same problem on a Compaq Presario C500 laptop. Exact same error messages. I did go to System -> Administration -> Hardware Drivers and chose to activate the B43 driver. It is working... though the error messages about the firmware still show up on boot and shutdown. I'd like to clear these so that I have a clean boot.

---

### Post by dcstar on 2009-12-01
> **spamking2000 said:**
> Hello,

I'm having the same problem on a Compaq Presario C500 laptop. Exact same error messages. I did go to System -> Administration -> Hardware Drivers and chose to activate the B43 driver. It is working... though the error messages about the firmware still show up on boot and shutdown. I'd like to clear these so that I have a clean boot.

Those messages contain explicit instructions, has anybody bothered to follow them?

---

### Post by barnaclebill18 on 2009-12-03
I went to the site listed in my error message and followed the instructions and the errors went away, I tried the wireless, but it said there were no networks, but I know there are.

---


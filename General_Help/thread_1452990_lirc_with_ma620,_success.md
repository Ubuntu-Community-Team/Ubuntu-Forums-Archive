---
title: "lirc with ma620, success?"
date: 2010-04-12
forum: General Help
---

### Post by imblack on 2010-04-12
Hello All,
I just want to know if there's any single user that had any success with configuring an MA620 IrDa with Lirc?

Thankyou very much,
If you need any details just let me know.

---

### Post by bartman2589 on 2010-09-12
Typically IrDA ports can not be used for remote control, they are designed to transmit and receive data using specific protocols embedded into the hardware (in most cases), because of this they don't recognize the signals from non-IrDA compliant devices (remote controls and other simple hardware), there have been a few exceptions of course to this (typically cases where the transfer protocols are solely based in the OS, or in the exceptionally rare instance where an IrDA port behavior can be mapped in the bios to that of a standard serial port instead of specifically an IrDA port).  In most instances to use an IrDA device to transfer data you need to use software specifically designed for it, lirc is not for data transfer but rather is designed to enable remote control of various features of linux (media apps, specific desktop features and so on).

You can use IrDA to connect to devices like printers that support IrDA connections by assigning the printer driver to connect to the port you have assigned to the IrDA interface (ttyS0, ttyS1, etc...), the same is true of using IrDA to synchronize files on things like PDA's and such, though you need an application that supports this of course.

I hope this helps clear up any misconceptions on what IrDA is for, as stated it's not for remote controlling a pc but rather for wireless data transfer (it predates wifi and bluetooth by a long shot) to/from external devices.

This link should provide more information on the limits of IrDA and how they affect using IrDA ports (even IrDA usb dongles) with lirc:

[http://www.lirc.org/irda.html](http://www.lirc.org/irda.html)

---

### Post by imblack on 2010-09-15
Thanks for your time, So
You mean that the communication protocol in dongles most probably is burned in hardware which limits the ability to receive signals from simpler devices like TV Remotes etc?

Coz I know these dongles work fine with mobiles and other data transfer things that support IrDa but they dont detect remote signals very good cause i have tried "cat /dev/ttyUSB0 > dump" where ttyUSB0 is where my device was attached in linux and it always shows same pattern of hex characters no matter what key i press.

---

### Post by bartman2589 on 2011-02-26
Sorry I didn't get back to you sooner, for some reason I didn't receive notification of your reply, but yes in most cases with IrDa interfaces the protocol handling is 'burned into' the hardware itself.  The key thing here is that data transfer (file transfer and the like) uses a specific protocol.  And most IrDa interfaces won't recognize and decode any signals that are not encoded using that protocol, I believe there are a handful that might allow for viewing the 'raw' data being received by the interface, which in theory if you can map that output to a virtual serial port then you could likely use lirc with that particular IrDa device.  Myself I'm using a homemade IR receiver that connects to a physical serial port on my computer to allow me to use the Windows variant of lirc called WinLirc to control Media Player Classic using a generic universal remote control.  If you have a physic serial port on your computer (usually won't work with most usb to serial adapters though) this may be a cheap way to go, assuming you're able to build the device yourself, otherwise you can dig around online for cheap USB versions or even old used Serial port versions of commercial remote receivers, I know Packard Bell and a number of other companies used to make serial port IR receivers that they sold with/without remotes, and of course there are many companies currently making USB IR receivers for use with Media PC's.  You can usually find the USB ones for less than $40US (some as cheap as about $20US even).  But if you want to try your hand at building your own serial port IR receiver (not really that hard to do actually), there are diagrams available on the LIRC site itself, as well as many other sites online.  Some of the diagrams even include an IR transmitter to allow you to send IR signals to some of your other devices to control them, like say turning on a TV, or starting a DVR, or changing channels on a cable box.

---

### Post by imblack on 2011-02-27
Man you are awesome, I lost hope but you came back :)

Thanks for your explanatory reply It clears everything. And Yes I would very much like to build my own receivers as I am fond of electronics as much as I am of programming :)

I will dig up diagrams and see what could be done, just please stay subscribed to this thread so I can ask you if I am stuck anywhere. 

Thanks Alot again, Have a good day!

---


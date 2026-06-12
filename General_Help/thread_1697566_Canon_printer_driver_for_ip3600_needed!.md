---
title: "Canon printer driver for ip3600 needed!"
date: 2011-03-01
forum: General Help
---

### Post by lamdis on 2011-03-01
Have been trying to install my canon ip3600 printer and followed all downloads available through site but errors inhibit installation; troubleshooting tips have not been unsuccessful;
any reliable beginners fix would be greatly appreciated. thanks

---

### Post by nomko on 2011-03-01
Did you get your drivers from here:
[http://software.canon-europe.com/products/0010648.asp](http://software.canon-europe.com/products/0010648.asp)
and here: [http://support-au.canon.com.au/P/search?model=PIXMA+iP3600&menu=download&filter=0&tagname=g_os&g_os=Linux](http://support-au.canon.com.au/P/search?model=PIXMA+iP3600&menu=download&filter=0&tagname=g_os&g_os=Linux)?

---

### Post by lamdis on 2011-03-01
have downloaded from sites described but printer still  silent ; any ideas on what to do greatly appreciated;
thanks

---

### Post by nomko on 2011-03-01
Do this:
 
- turn printer on.
- open a terminal
- type in: **lsusb**
- place the output here

---

### Post by lamdis on 2011-03-01
typed at the terminal command described then realized unable to place output due to knowledge lacking; your indulgence at this juncture : thanks!

---

### Post by nomko on 2011-03-01
> **lamdis said:**
> typed at the terminal command described then realized unable to place output due to knowledge lacking; your indulgence at this juncture : thanks!

It's simple to do a copy and paste:
In the terminal select all the text you want to copy and right click and select in the pop-up menu **Copy**. 
And then you can paste it here with Ctrl+V

---

### Post by lamdis on 2011-03-01
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by nomko on 2011-03-02
> **lamdis said:**
> Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 
 
That's it?? Nothing more?
How many usb devices have you connected to your pc?

---

### Post by lamdis on 2011-03-02
One

---

### Post by nomko on 2011-03-03
Okay, and you performed this command with your printer connected and turned on? 
 
Since i just see 2 hubs (most likely the USB ports at the back of your pc) i think there's much more wrong then a non-working printer.

---

### Post by lamdis on 2011-03-05
Got it working with the canon ip4600 driver; I guess the ip3600 driver is not installed properly.
many thanks

---

### Post by johanbove on 2011-07-01
Hi, thanks for this interesting info. What Ubuntu version are you using and are you using 32-bit or 64-bit OS?

---


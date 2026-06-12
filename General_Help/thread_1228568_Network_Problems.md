---
title: "Network Problems"
date: 2009-08-01
forum: General Help
---

### Post by Nater43 on 2009-08-01
Well, I've enjoyed the help I have received so far, but its been a pain switching from Windows to Ubuntu, just to check for new post about my troubles. I cannot seem to get a wireless connection running in Ubuntu. 

I have a Linksys WRT110 router, and a Belkin 802.11g Network Adapter.

---

### Post by Bucky Ball on 2009-08-01
First thing: have you plugged an ethernet cable in an gotten any updates and restricted hardware you might need to get the wireless going? If not, do that now. :)

---

### Post by Nater43 on 2009-08-01
I have an ethernet cord plugged in now, but where should I go/look for the updates you speak of?

---

### Post by Bucky Ball on 2009-08-01
System->Administration->Update Manager

---

### Post by Nater43 on 2009-08-01
Just ran through that, but still nothing with the wireless. I set up the network, but it just won't connect. Next to the wireless network it says "never." I have no idea if that might have something to do with it.

---

### Post by Bucky Ball on 2009-08-01
Internal wireless card I presume. Do you know what? If not, type:

```
lspci
```

... in a terminal. Somewhere near the bottom it should tell you. Also, could you check in:

> System->Admin->Hardware Drivers

Is there anything driver there pertaining to your wireless card, disabled perhaps?

---

### Post by Bucky Ball on 2009-08-01
Also, in System->Admin->Network, unlock and check the properties of your wireless device. Is that enable roaming set top left? If so, unclick, set name of your network, WEP or WPA security key and Configuration to 'Automatic Configuration (DHCP)'.

Now go to the router and make sure all details match the ones on the mache and that it is set up as a DHCP server. 

It is essential you have the details set on the router, especially DHCP server or not. If you have your machine set up with a STATic IP and the router as a DHCP server it will never connect as they are trying to jam an IP down each other's throats.

If you want to set up static, it is best to go with the DHCP first just to make sure you have a connection, then change it. I can show you how (along with plenty of others around here!).


* When making changes, you will need to type this:

```
sudo /etc/init.d/networking stop

sudo /etc/init.d/networking start

```
... one line at a time (not both at once) in a terminal for the changes to take effect. 


Good luck. :)

---

### Post by Nater43 on 2009-08-01
With going into Hardware Drivers, I enabled the proprietary driver for the Broadcom card. I then tried disconnecting the wired connection, but it didn't connect to the wireless. I can't seem to find the unlock thing that you mentioned. I triple checked the connection that I set up, and the WPA code was correct. Named correctly. Set to auto connect. Still nothing.

---

### Post by Bucky Ball on 2009-08-01
Leave that ethernet cable in. The broadcom driver needs to install b43fwcutter to work. Just wait until you have the wireless up before disconnecting the cable. :)

I would perhaps shut down, plug in cable, boot into Ubuntu and run update again. Give it a minute or two to identify your card and the Broadcom driver and it may prompt you with a message that you need to install other software. 

Are you using 9.04 or 8.04?

---

### Post by Iowan on 2009-08-01
> **Nater43 said:**
>  Next to the wireless network it says "never." I have no idea if that might have something to do with it. That's indicates the last time the interface was used. "Never" means it hasn't been used before.

---

### Post by Nater43 on 2009-08-01
I'm using 9.04.

---

### Post by chessnerd on 2009-08-01
Have you tried checking the manufacturers website for Linux drivers? Some companies have started to provide them and this was how I finally got a printer to work on my Linux system. (This, of course, assumes that the driver is the problem.)

Also, here's a (very) extensive guide to setting up your wireless using CLI: [http://www.ubuntugeek.com/how-to-troubleshoot-wireless-network-connection-in-ubuntu.html](http://www.ubuntugeek.com/how-to-troubleshoot-wireless-network-connection-in-ubuntu.html)

Hope one of those helps.

---

### Post by Nater43 on 2009-08-01
I don't know what I did, but I just figured I'd pull the ethernet cord out, and try the wireless out. It decided to work!

---


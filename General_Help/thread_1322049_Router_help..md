---
title: "Router help."
date: 2009-11-10
forum: General Help
---

### Post by Transmutation on 2009-11-10
So just a few days ago I switched from cable to Embarq phone and internet, but the the problem is the router they gave me only fits one plug and thats for the internet cable and I need more then 1 slot.  So my friend gave me a router that was lying around, a Linksys etherfast cable/dsl router with 4-port switch but I have to run a disc first to get it working, but heres the problem nothing pops up and well my disc basically isn't read and yeah I need to install this new router but I can't.  Any suggestions?  I don't know much about computers so yeah...if you can help keep it simple please?

---

### Post by Transmutation on 2009-11-10
Any help?

---

### Post by jbrown96 on 2009-11-10
You don't need to run that disk. Attach your computer to the router and go to 192.168.1.1 The default username is admin and the password is blank. If those credentials don't work, hold the reset button on the back for 20 seconds.

---

### Post by prem1er on 2009-11-10
You shouldn't need to install any software in order to get a router to work. Just plug in the router and in a browser go to 192.168.1.1. This is your routers admin page and you can edit any settings you need changed in there.

---

### Post by QIII on 2009-11-10
It might be possible to download (yes, that may be a bit difficult for you without service right now!  You may have to do this at a buddy's machine) a Linux-specific driver for the hardware from the OEM's website.

Alternatively, many routers allow you to do the setup from firmware on the router itself (for instance, some Netgear routers require only that you type something like "http:/www.routerlogin.net") into your browser, which will allow you to configure the router in a browser-based application.

If you can, use someone else's system to go to the OEM website and see what you can gather from them.

---

### Post by cgb on 2009-11-10
Like the others said you dont really need the installation disk.  Just connect your computer to the Router and open your browser to the IP address suggested.  If you are planning on basically just using this router as a switch to gain extra ports alongside the other router the ISP provided, then you are probably best to just disable DHCP on the new router.  With just changing this setting it will basically just act as a switch and you would want to actually plug the cable coming in from the other router into one of the LAN ports and not the WAN port.  This would be the simplest setup.

---

### Post by Transmutation on 2009-11-10
I tried the suggestions but the thing is the router I got from the company only fits one ethernet cord and thats where we have our internert cord in and if I disconnect it and put it on the other router and connect both routers I can't get online, so yeah...nothing works so idk I'm kinda get mad right now since I can't figure out what to do now.

---

### Post by Transmutation on 2009-11-10
Could someone please explain this to me in detail step by step?

---

### Post by QIII on 2009-11-10
OK.  To clarify.

Did your ISP give you a ROUTER or a MODEM?

---

### Post by norm7446 on 2009-11-10
Ok,
1) plug in your new router the start the PC up.

2) Once you are logged in. Start your Internet browser of choice ie: Firefox.

3) In the address bar type 192.168.1.1 and press return. This should bring up the on-board webpage for your router. From here you should be able to input your internet user name and password that was given to you by your ISP. Once this is done you should be up and runnig on the new router.

---

### Post by Transmutation on 2009-11-10
A router, it says so in the bottom of it.  Whats the difference between a modem and a router?

---

### Post by Commander_Keen on 2009-11-10
Think of Router as a splitter.
Modem: converts the single from the ISP into usable data 
Google it.

---

### Post by Transmutation on 2009-11-10
My bad its a modem.  But I want to connect a router to it so I can plug in more stuff but the thing is it has only one ethernet port and thats for my internet and my computer only has one ethernet port also and thats were the other end of my internet cable is plugged in.

---

### Post by QIII on 2009-11-10
You have a router with one hole for a power source and only one other "hole"?

---

### Post by Transmutation on 2009-11-10
> **QIII said:**
> You have a router with one hole for a power source and only one other "hole"?

Read my post above.

---

### Post by cgb on 2009-11-10
Okay, unplug the Modem (the device your ISP gave you) from the power cord.  Plug the one ethernet cable that comes from the Modem into the WAN port on the Router.  Then plug another cable from any of the 4 LAN ports on the Router into your computer.  Now plug the power back into the modem.  The reason we unplugged it is due to the fact that most DSL modems lock onto MAC address's and this is the only way to get it to lock onto the new MAC address of the Router.  Chances are everything should just work with no other settings but let us know if you still have no success..

---

### Post by QIII on 2009-11-10
OK.  Hold on.  I'll try to do this graphically.  I'm trying to follow what you are saying, but I don't think we are talking the same language.

Modem:     
power --> 
                 internet in -->
                 <---ethernet out 
                 |
                 V
Router
--->ethernet in   (This port should specify "Internet" or similar)
                 <---ethernet out 
                 |
                 V
Computer
---> ethernet in

---

### Post by Transmutation on 2009-11-10
Thank you everyone!  It's all fixed now! :D

---

### Post by QIII on 2009-11-10
If you are still around...

Be sure in your setup that you have been very aggressive in your security settings.  Consult the manual carefully.

You should be able to use a firewall on the router as a first line of defense, but don't depend on it alone.

---


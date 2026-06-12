---
title: "Setting up Windows Printer on Natty"
date: 2011-09-05
forum: General Help
---

### Post by moorhead98 on 2011-09-05
is there any easy way to _wirelessly_ setup a printer on ubuntu?
The printer was installed on windows, and i cant seem to get it to install correctly on my ubuntu laptop (running 11.04).
The printer is a Hp Officejet Pro L7680 All in one printer.
Any ideas?

---

### Post by dino99 on 2011-09-05
HPLIP does support your printer. (should be already installed, see synaptic)

---

### Post by coffeecat on 2011-09-05
@moorhead98, the driver for your HP Officejet Pro L7680 is included in a default install of Ubuntu 11.04. So long as it is correctly connected wirelessly to your router, and your Ubuntu system is connected to the router then it should be easy to set up.

Open the Unity dash, type "print" in the search bar and open the Printing utility. Click on Add and then wait a minute or two. It can take some time for a network printer to appear in the Devices list. If it appears, highlight it and click on the Forward button.

What problems are you encountering?

---

### Post by moorhead98 on 2011-09-05
> **coffeecat said:**
> @moorhead98, the driver for your HP Officejet Pro L7680 is included in a default install of Ubuntu 11.04. So long as it is correctly connected wirelessly to your router, and your Ubuntu system is connected to the router then it should be easy to set up.

Open the Unity dash, type "print" in the search bar and open the Printing utility. Click on Add and then wait a minute or two. It can take some time for a network printer to appear in the Devices list. If it appears, highlight it and click on the Forward button.

What problems are you encountering?

Well the major problem I am encountering is not being able to print anything.

Joke aside, I go into add printer, and put all the information for the windows printer. I am 90% sure that I am putting the information in right, but it still doesn’t work.
Also, I am not sure if I am going to the right place when adding the printer.
Should i go to the one that says "Windows Printer Via Samba"? or somewhere else?

---

### Post by coffeecat on 2011-09-05
Ah - perhaps I misunderstood your setup. I thought you had the printer connected to your network. From your last post it sounds as though it's connected to your Windows machine by USB and you want to print via the Windows machine from your Ubuntu machine. Or have I got you wrong again? 

Doing a bit of googling I see that the printer is not a wireless one after all, but does have networking capabilities via ethernet. Why not simply use it as a network printer? This is how I have my HP OfficeJet (different model) set up. It's connected to my router via ethernet and it "just works" from Windows, Ubuntu and my Mac Mini.

---

### Post by moorhead98 on 2011-09-05
> **coffeecat said:**
> Ah - perhaps I misunderstood your setup. I thought you had the printer connected to your network. From your last post it sounds as though it's connected to your Windows machine by USB and you want to print via the Windows machine from your Ubuntu machine. Or have I got you wrong again? 

Doing a bit of googling I see that the printer is not a wireless one after all, but does have networking capabilities via ethernet. Why not simply use it as a network printer? This is how I have my HP OfficeJet (different model) set up. It's connected to my router via ethernet and it "just works" from Windows, Ubuntu and my Mac Mini.

What I want to be able to do is print from my Ubuntu Laptop. The printer was set up on windows, so I figured I would have to go to "Windows printer via SAMBA".
I cant say for sure thats the right option. 
I believe that it is a network printer, but im not 100 percent sure. Is there any way to check this?

---

### Post by coffeecat on 2011-09-05
> **moorhead98 said:**
>  
I believe that it is a network printer, but im not 100 percent sure. Is there any way to check this?

[http://h10010.www1.hp.com/wwpc/us/en/sm/WF06b/18972-18972-238444-12019-3328086-3601422-2511714-2511715.html](http://h10010.www1.hp.com/wwpc/us/en/sm/WF06b/18972-18972-238444-12019-3328086-3601422-2511714-2511715.html)

Under Connectivity, standard: "1 Ethernet".

If it has an ethernet port, it's a network printer. The manual should tell you anyway.

---

### Post by moorhead98 on 2011-09-05
> **coffeecat said:**
> [http://h10010.www1.hp.com/wwpc/us/en/sm/WF06b/18972-18972-238444-12019-3328086-3601422-2511714-2511715.html](http://h10010.www1.hp.com/wwpc/us/en/sm/WF06b/18972-18972-238444-12019-3328086-3601422-2511714-2511715.html)

Under Connectivity, standard: "1 Ethernet".

If it has an ethernet port, it's a network printer. The manual should tell you anyway.

Well then it is a network printer.
Now how do I set it up?

---

### Post by coffeecat on 2011-09-06
> **moorhead98 said:**
> Well then it is a network printer.
Now how do I set it up?

Connect it to the router with an ethernet cable, switch it on and follow the procedure in Ubuntu that I outlined in post #3.

---

### Post by moorhead98 on 2011-09-17
> **coffeecat said:**
> Connect it to the router with an ethernet cable, switch it on and follow the procedure in Ubuntu that I outlined in post #3.
I think i found the problem. To access the printer you need to be granted it by the admin account on windows, or something like that.

---

### Post by moorhead98 on 2011-09-18
Scratch that... I think its the same problem we had before.
Does it have to be a specific ethernet cord for the printer or just a run-of-the-mill cord?

---

### Post by coffeecat on 2011-09-18
So long as its good quality run-of-the-mill. :) Most of the quality ones have "CAT 5e" printed on the insulation.

---

### Post by coffeecat on 2011-09-18
@moorhead98, I meant to add something and forgot. First - good luck with networking the printer. It's much the best option - imo.

When I first set up mine about a couple of years ago, Ubuntu got a bit muddled when the network IP address of the printer changed, if I powered up computers and devices in a different order. That's with the printer set up to accept dynamic IP addresses by DHCP, which is the default. If you have a Netgear router, you can assign a static IP address to a particular host from the router. Some other makes of router, such as Linksys, don't have this and you have to assign a static IP address in the printer itself. This is not documented in the HP manual - at least not with mine - but I found a way of doing it. Post back if you need details.

---

### Post by moorhead98 on 2011-09-18
> **coffeecat said:**
> @moorhead98, I meant to add something and forgot. First - good luck with networking the printer. It's much the best option - imo.

When I first set up mine about a couple of years ago, Ubuntu got a bit muddled when the network IP address of the printer changed, if I powered up computers and devices in a different order. That's with the printer set up to accept dynamic IP addresses by DHCP, which is the default. If you have a Netgear router, you can assign a static IP address to a particular host from the router. Some other makes of router, such as Linksys, don't have this and you have to assign a static IP address in the printer itself. This is not documented in the HP manual - at least not with mine - but I found a way of doing it. Post back if you need details.
My router is a Netgear router. How do I set the static Ip address? and is there a specific order to start up the computers?

---

### Post by coffeecat on 2011-09-18
Your Netgear router will have its own IP address of 192.168.0.1 and will assign IP addresses to hosts within the range 192.168.0.X, probably starting with 192.168.0.2. Each attached device is assigned a lease which expires after a certain period. If it is still connected at that time, the lease is renewed, otherwise that IP address is available if another device comes on line. The router will simply assign available addresses in numerical order, so if you switch devices on and off, you will see IP addresses change.

In a Netgear router, you can see what devices are attached, their IPs and MAC addresses under "Attached Devices" in the admin interface. LAN setup > Address Reservation allows you to - well - reserve an address. If you click on the add button, you can reserve the address the device already has, or you can assign an IP of your choosing. You can get to the admin interface by typing "192.168.0.1" in your browser address bar and logging in. The default name and password are what is in the manual - ("admin" and "password" if I remember correctly!) or you may have changed these already.

---

### Post by moorhead98 on 2011-09-26
I solved the problem. I'll write the process for anybody else who has this problem:
1) I went to the windows printer, and changed the share name of the printer to one **_WITHOUT _**spaces (and also turned off password protection sharing or something in windows sharing options)
2) I went to add printer (on Ubuntu)
3) then network printer
4) then windows printer via samba
5) next i hit browse and found the printer
6) hit verify (might not be necessary actually)
7) did the next step and installed drivers
8 ) printed a test page
9) watched in awe as it printed!

---

### Post by apkern on 2011-09-30
You can also put a %20 to cover the spaces. That's what I had to do when I ran CUPS with localhost:631 in a browser window and checked the naming convention of the printer driver. Had to put a % in front of the 20's (blanks) that were listed. Worked like a charm as I've been fighting with it for about three days now.

---

### Post by SNIFFER_dog on 2011-10-05
Thanks moorhead98 & apkern,

The spaces in my windows printer name caused the problem for me too. In the Samba address in Ubuntu 11.04 the % was missing in front of the various '20's which matched the location of the spaces in my windows printer name.

I decided to delete the printer I had set-up in Ubuntu and start again. This time when I checked the address the % were missing but I could not for some reason add them in the initial set-up window.

I decided to just continue with the set-up, and then once it was finished I could easily add the % into the settings for the address of my printer.

Thanks again for this, such a simple little thing but without the knowledge I would have been stuck with no printer for ages.

Many thanks for the tip,

SNIFFY

---


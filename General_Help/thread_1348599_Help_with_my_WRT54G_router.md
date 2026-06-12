---
title: "Help with my WRT54G router?"
date: 2009-12-07
forum: General Help
---

### Post by JoeyF on 2009-12-07
I installed Ubuntu 9.10 and the router works fine. Problem is i forgot the password and i want to use my PS3 wireless.


Here are the instructions i got from Linkys:
```
: Steps on how to reconfigure the WRT54G for DSL connection:

 Plug in this computer to any of the regular ports (any of the port 1-4) of the router using an Ethernet cable. Connect the router to the modem.

 Press and hold its reset button (located at the back of the router) for 30 seconds and then unplug and replug the power cord from it.. That is how to reset the router.

 Even without Internet connection, access the setup page of the router. To do that, open an Internet Explorer page or any type of browser. On the Address bar, type: 192.168.1.1, then hit Enter. If a log-in screen will appear, please type admin for the Password and leave the User Name blank or empty, then hit OK. (Note: By default, the setup page should be accessed even without Internet.)

In the routers setup page, click on the Setup tab and go to the Basic Setup sub tab. Make sure to set the "Internet Connection Type" to DHCP (Obtain an IP Automatically). Save settings.

 Still under the Setup tab, click on the MAC Address Clone sub tab. Click on "Clone your PC's MAC" then save the settings.

 Incase you also want to configure the settings for your wireless network, click on the Wireless tab, and then enter the following settings:

Wireless Mode: Mixed

SSID: your name or anything except linksys

Channel: 11

SSID Broadcast: Enable

 So to secure your wireless network, click on the Wireless Security tab (next to the Basic Wireless Settings sub tab).

 Set the Wireless Security mode to WPA Personal. Set the Encryption to TKIP.

 Leave the other settings on default. For the WPA Shared Key, enter there your wireless network password. It should be at least 8 characters; a password that will be easy to remember, but difficult for others to guess. Secure a copy of that password just incase you forget it in the future.

 Click on Save Settings button below.

 Go back to the Basic Setup sub tab under the Setup tab, and then change the Local IP Address to 192.168.2.1. This is to avoid conflict against the IP address of your modem. Save settings.

 Shut down everything for 5 minutes, starting from the computer, then, the router, and lastly, your modem..

 Power on (starting from the modem, then the router and lastly this computer).
```

Problem is i can't get 192.168.1.1 to come up, 

Any help? I don't have the disk.

Thanks,
*Note, I haven't tried resetting it before entering the IP. I just don't want to reset it and it not work(Don't want to lose my wireless on my Laptop running Windows(I'm on a desktop for Linux), In other words, I want to be sure it will work before i reset it)

---

### Post by pbrane on 2009-12-07
if you are on the same router wireless in windows then all you need to do is configure the PS3. One way to make sure that the router default address hasn't changed is to look at the address on your computer. If it isn't 192.168.1.something then the default IP has changed. Also it is possible to disable wireless administration of the router. Mine is setup that way. You have to physically plug in to make any changes. The default username is 'admin' and password is 'admin' for that router. Oh and you are trying that IP in a web browser, right?

---

### Post by JoeyF on 2009-12-07
> **pbrane said:**
> if you are on the same router wireless in windows then all you need to do is configure the PS3. One way to make sure that the router default address hasn't changed is to look at the address on your computer. If it isn't 192.168.1.something then the default IP has changed. Also it is possible to disable wireless administration of the router. Mine is setup that way. You have to physically plug in to make any changes. The default username is 'admin' and password is 'admin' for that router. Oh and you are trying that IP in a web browser, right?

I can't set it up because i can't remember the pass. the router is plugged in to my Desktop running 9.10. How can i find out the address for it?

ANd yes i am doing it in Firefox.

Thanks,

---

### Post by nikhilbhardwaj on 2009-12-07
my router is so crappy
that it resets the password to admin
each time i turn it off

but yes a reset does work
however if you are unsure
there's an option which allows you to save your current config in a file and import it later

---

### Post by underquark on 2009-12-07
Some routers have a little reset switch at the back - switch off, poke a blunt object into the button and hold in for 10 seconds or so whilst switching router back on.  Apt to reset everything, though, so make sure you know your ISPs connection settings etc.

---


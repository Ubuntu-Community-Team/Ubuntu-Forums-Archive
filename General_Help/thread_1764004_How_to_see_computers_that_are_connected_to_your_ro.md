---
title: "How to see computers that are connected to your router?"
date: 2011-05-21
forum: General Help
---

### Post by Karlas on 2011-05-21
Hello,
How can I see computers that are connected to your router?
I need to see detailed info,like IP and stuff.
Thank you

---

### Post by kerry_s on 2011-05-21
that would be in your router's web ui.

---

### Post by TeoBigusGeekus on 2011-05-21
Get inside your router with an internet browser (192.168.0.1, etc.) and check devices, home network and such.

---

### Post by 3xp10r3r|X13 on 2011-05-21
I really nice program to see all connections going on is "ether ape". you can install it using your regular software center. (It's a graphical network monitor, so a bit more user friendly than the terminal ones)

or just type:

sudp apt-get install EtherApe 

Try it out :)

---

### Post by lisati on 2011-05-21
Figuring out who is connected to your network can depend on your router.

On my Netgear router's admin panel, it's "Attached devices". On my modem/router (a "freebie" by Thomson/Speedtouch from my ISP), its on "Home Network"

---

### Post by Karlas on 2011-05-21
> **TeoBigusGeekus said:**
> Get inside your router with an internet browser (192.168.0.1, etc.) and check devices, home network and such.
Umm its keep loading,but then it says "Problem loading page" I tried entering my IP but no luck

EtherApe doesnt work either I get this error "Error getting device: no suitable device found"

btw Im using eth,not wlan
I have a very simple router,it only shows whos connected with wired network,not with wlan,

Any suggestions?

---

### Post by linuxinstalledfromhdd on 2011-05-21
call tech support for the manufacture of your router.. start a trouble ticket and you will have faster than through ubuntu forums. :p

---

### Post by crispy_420 on 2011-05-21
As for etherape, run with sudo (sudo etherape) command and stop the capture. Select the interface (NIC) to capture from and start the capturing again. But this will show only systems using the network right then (browsing, pinging, etc.). If the device is only listening it will go unnoticed. But any active connection will show, type of connection (protocol) and source/destination.

To search for devices listening, use something like nmap or angry ip scanner. These will show devices listening on your LAN and depending features enable you can get OS type, hostname and open ports. You just have to enter the range (Angry IP Scanner) or the broadcast address with subnet bits (nmap). So a typical home network range would be 192.168.1.1/24.

You concerned about unauthorized devices?

---

### Post by Mark Phelps on 2011-05-21
> **Karlas said:**
> 
I have a very simple router,it only shows whos connected with wired network,not with wlan,

Any suggestions?

On my Linksys router web page, there is an Administration tab.

Under that, there's a Local Network tab.

On that, there's a DHCP Client table button.

Clicking that lists out all the local network addresses assigned by the router.

Look to see if you have something similar.

---


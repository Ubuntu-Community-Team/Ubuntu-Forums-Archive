---
title: "Yet another pppoe problem, but this time it's a little different form the rest"
date: 2006-01-23
forum: General Help
---

### Post by raid996 on 2006-01-23
Ok, I have a notebook, just as mine that I have to connect to the web.
This notebook is connected to a ethernet adsl modem, the modem is dhcp capable and after running ppoeconf and giving name and password I had all running even after reboot (already went through that with another pc).
My problem is another one, the connection is not a flat type, which means that I pay for the amount of time I spend on the internet, so actually I need to have my pc to connect and disconnect when I say so and not when it starts up.

I tried not to set up the connection on startup but after I type "pon dsl-provider" it won't work.
I managed to have it working after many try outs but the problem is this friend of mine (who has no idea about linux) has to open System->Administration->Network, activate the eth0 interface then type:

pon dsl-provider
plog
ifconfig ppp0

otherwise it won't work (yes, the last two included, i tried it!!!!)
How can I have some sort of network administrator that could allow me to just connect by clicking a button or at least but typing only one line of command??
I remember I set it up just fine with KDE through all graphic tool...now having trouble with ubuntu distro.
I just need to have the connection steps easier for this friend of mine... some1?!?!?!!:confused: :confused: :confused: :confused: :confused:

---


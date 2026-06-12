---
title: "want to make ubuntu wired/wireless router"
date: 2011-03-07
forum: General Help
---

### Post by jewfromdahood on 2011-03-07
I have a netgear wndr3700 router and love it, and then I thought I have an old pc i built, with a intel P4 650 x86_64 with like 2.5 or 3GB RAM, and 1 80 GB master, and 2 320GB slaves. and I was thinking. I could make a kick *** router with it. I would like to make a linux router out of it. I'm going to buy a D-link DWA-556 pci-e wireless card, add a better antenna to it, put in a 1GB ethernet NIC, to attach to a netgear switch, and throw in a huge seagate 1.5TB or more HD in conjunction with the other HD's already there (case I had could fit 6 HD's) but I need it to do several things may be a little out of order as I am typing as I remember what I wanted, I thought about using distcc, but on a slower desktop compared to my core 2 laptop I figured I wouldn't
1) firewall
2) N wifi router with WPA2
3) wired router via 1000MB PCI slot NIC connected to 5 port switch
4) NAS so it acts like another hard drive so I can store more videos
5) UPNP
6) ushare for my xbox 360 but not only needs to share videos. But also want it to share my music. thus the large hard drives
7) control over txpower on the wifi like in DD-WRT
8 )web ui
9) QoS
10) port forwarding and all other router goodies
11) apt-get cache server
12) dns cache server
13) dhcp
14) possibility to share printers over the LAN to not just ubuntu setups, but windows and mac, as I have a lot of family that visits. Printer will of course be HP because they have by far in my lifetime given me the second best experience, (first being xerox I had a phaser 8400 and it was kick ***, solid ink printer)
basically I want it to do everything dd-wrt does, graphs of bandwidth and everything, but with a few more goodies.
Most likely I would put this router on a desktop version of ubuntu as it would be connected via vga to my lcd tv with keyboard and mouse, for when cousins come over and they want to use a computer. I don't let them touch my laptop as it is my baby and i built her.

---

### Post by robsoles on 2011-03-07
(1) Are you asking for help to do all of that or are you bragging?

(Just secretly between you and me, I'd use the netgear modem/router connected **only** to 100Mb/s ethernet port on the server and I'd connect my LAN via a 1Gb/s ethernet port and then I'd apply most of everything else of your list - firewall in modem/router adds layer of defense, firewall in server should be configured as if it is 'the last line' of NAT etc...)

(2) I would recommend setting your server aside and not letting anybody use it 'locally' for any purpose - it is best kept as specific remote access for authenticated users and routing and other service provision to your LAN. My server hasn't a monitor and won't get use of one till I can't SSH in anymore, it's in the corner of my bedroom...

If you are just bragging this belongs in the Community Cafe but if you are asking for help to do all that then I'm going to suggest you break it down into a logical order in which to accomplish each required configuration and start a thread with the first one you get stuck on.

Before you decide you are stuck on one make sure you've tried the problem using an ubuntuforums.org specific search with Google: [http://www.google.com/search?client=ubuntu&q=site%3Aubuntuforums.org+what+is+my+question+again]("http://www.google.com/search?client=ubuntu&q=site%3Aubuntuforums.org+what+is+my+question+again")

???

---

### Post by aeiah on 2011-03-07
i suggest you make sure the wireless card you plan on using can be used in AP mode, if you insist on not using a router. i know generally atheros chipsets are generally good for that sorta thing.

to be honest, since you're spending so much money anyway id consider getting a good dd-wrt wireless N router to act as the access point. ive got an excellent buffalo dd-wrt router that cost about £50, but its only wireless G. a lot easier to manage than having a pci-e wifi card. and it has two radios and a massive amp for diversity and range.

---

### Post by jewfromdahood on 2011-03-07
> **robsoles said:**
> (1) Are you asking for help to do all of that or are you bragging?

(Just secretly between you and me, I'd use the netgear modem/router connected **only** to 100Mb/s ethernet port on the server and I'd connect my LAN via a 1Gb/s ethernet port and then I'd apply most of everything else of your list - firewall in modem/router adds layer of defense, firewall in server should be configured as if it is 'the last line' of NAT etc...)

(2) I would recommend setting your server aside and not letting anybody use it 'locally' for any purpose - it is best kept as specific remote access for authenticated users and routing and other service provision to your LAN. My server hasn't a monitor and won't get use of one till I can't SSH in anymore, it's in the corner of my bedroom...

If you are just bragging this belongs in the Community Cafe but if you are asking for help to do all that then I'm going to suggest you break it down into a logical order in which to accomplish each required configuration and start a thread with the first one you get stuck on.

Before you decide you are stuck on one make sure you've tried the problem using an ubuntuforums.org specific search with Google: [http://www.google.com/search?client=ubuntu&q=site%3Aubuntuforums.org+what+is+my+question+again]("http://www.google.com/search?client=ubuntu&q=site%3Aubuntuforums.org+what+is+my+question+again")

???

asking for help, wanted to list hardware, in case of incompatibilities and further help to get it done. Well I do have 2 older pcs not being used. Problem is the 2nd one, is lower performing, no pcie and no sata so I can't get a huge hd for it. and it's PCI only. I refrain from using PCI on more than 1 device as that 133 MB/s bandwidth on pci is shared amongst all devices. and PCIe is dedicated. So I will be using PCIe preferably. because I want full N wifi use. and I have an intel 5300 abgn on my laptop and due to a bug N use is disabled, and when I enabled it, the connection crapped out after an hour or two and had to keep resetting.
Also wondering is there a good wifi card with detachable antenna's that has 5Ghz N, as I would like both 2.4Ghz and 5Ghz. I want detachable so I can attach a better antenna for when friends of mine are outside in the summer in the backyard, as we like to use our computers outside and smoke a little hookah (nargilla) smoke cigars, etc. So I was thinking of adding another 2.4Ghz N card, for outdoor use attached to an outdoor antenna. 
But regardless; 
1) I'm going to install Ubuntu amd64 (as it supports 64 bit which is why I want to use it). Set up the router first after that is installed. I wonder if DD-WRT can be run on top of a linux OS, as it is a linux. That might simplify things. Once everything is set up the AP's the wired router part, QOS, WPA2, port forwarding, firewall, UPNP, dhcp, etc. 
2) I want to create the DNS cache part so all my dns queries are cached. with default dns's being opendns (208.67.222.222, 208.67.220.220) many people may ask why cache it, and I just always have wanted to, and it can reduce my wait time for pages.
3) create apt-get cache server, as I retrieve a lot of files. from repositories
4) Create the NAS and ushare part of this server, so it can be used with my xbox 360 for videos, and music, as well as store my files for my laptop and desktops, as I have a lot of music, and video, as well as source code, and compiled source code I keep, (source code alone from custom kernels and other things are around 100GB) but for some reason I can not share my music to my 360 only videos.
5) then finally get printers to be shared. I know Ubuntu will share printers to other Ubuntu computers, that's not an issue, but it needs to share with Macintosh and PC's as friends come over and so does family.

---

### Post by jewfromdahood on 2011-03-07
> **aeiah said:**
> i suggest you make sure the wireless card you plan on using can be used in AP mode, if you insist on not using a router. i know generally atheros chipsets are generally good for that sorta thing.

to be honest, since you're spending so much money anyway id consider getting a good dd-wrt wireless N router to act as the access point. ive got an excellent buffalo dd-wrt router that cost about £50, but its only wireless G. a lot easier to manage than having a pci-e wifi card. and it has two radios and a massive amp for diversity and range.

I already have DD-WRT on my Netgear WNDR3700, I love it. But this is just something I always wanted to do on my own. and I have an old PC I built for gaming, that well is only gathering dust. So I figure why not make a really powerful robust router and server out of it? Just for the sake of saying I can do it. I love to tinker and come up with new projects. Which is why I love linux. I tinker with the software so much. This server would be an educational project for me, and I am starting college soon getting my degree in computers, and why not do something that will blow everyone else out of the water. 

I wish Sony hadn't fracked up the linux opportunities, as I would have loved to have built a server from a PS3.

Plus my router will be big and made of aluminum and have the internals glowing blue.

---


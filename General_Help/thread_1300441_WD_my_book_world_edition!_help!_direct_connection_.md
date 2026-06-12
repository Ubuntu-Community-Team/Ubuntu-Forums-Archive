---
title: "WD my book world edition! help! direct connection with laptop"
date: 2009-10-25
forum: General Help
---

### Post by samsamros on 2009-10-25
I just bought a WD My Book World Edition II external drive it's great over the network but today i tried plugging it in my Dell XPS 1330 with ubuntu 9.04 and went completely undetected! it just recognized it as a wired network... I was browsing around some other websites that suggest that the solution is a crossover ethernet cable. Is this true? I'm trying to plug it in directly to the ethernet of my laptop, will it work as an external drive and will I be able to access my files without doing anything else beside plugging it in? thank you all in advance

---

### Post by JillSwift on 2009-10-25
You essentially have to make a hubless/switchless network to hook it up like that. That would require a crossover Ethernet cable.

The NAS needs to be configured to have it's own static IP address, as does your laptop (or your laptop needs to be able to serve a DHCP request).

[s]However, it looks liek the WD My Book World Edition II has a USB port. Use that to hook it up directly to your laptop for a far easier solution.[/s] Never mind, wrong direction.

---

### Post by samsamros on 2009-10-25
firs of all thank you for your answer, so basically you do need a crossover cable. but i still have a question with > 
The NAS needs to be configured to have it's own static IP address, as does your laptop (or your laptop needs to be able to serve a DHCP request) if you could kindly tell me how to do this. thank you in advance

---

### Post by WorldTripping on 2009-10-25
My NAS can be used either on the network via the router cable or as a standalone unit using the USB cable.

Does the WD not have a USB port you can link via?

---

### Post by JillSwift on 2009-10-25
> **WorldTripping said:**
> My NAS can be used either on the network via the router cable or as a standalone unit using the USB cable.

Does the WD not have a USB port you can link via?
It only has a "host" for expansion, no "guest".

---

### Post by JillSwift on 2009-10-25
> **samsamros said:**
> firs of all thank you for your answer, so basically you do need a crossover cable. but i still have a question with  if you could kindly tell me how to do this. thank you in advance
I'm sorry, but I don't know how.

---

### Post by WorldTripping on 2009-10-25
> **JillSwift said:**
> It only has a "host" for expansion, no "guest".

Ah, OK. Different boxes I guess.

> **samsamros said:**
> firs of all thank you for your answer, so basically you do need a crossover cable. but i still have a question with  if you could kindly tell me how to do this. thank you in advance

Sorry, I don't know either.

---

### Post by Wharf Rat on 2009-10-25
I purchased a Netgear 5 port mini hub and a couple of ethernet cables.

As my DSL wi-fi modem does DHCP I assigned the NAS an ip# outside of the DHCP range -  reserved on the wi-fi modem.

Example
Modem supplies 192.168.1.1 through 192.168.1.50
I assigned the NAS 192.168.1.100  via web browser and admin screen.

I can mount a NAS folder by FTP, SAMBA, or NFS.

So far, SAMBA is lacking.
FTP works the best for me and NFS is a bit frustrating.

I have yet to get ANY backup software to work correctly. So I resort to manually copying files.

---

### Post by Wharf Rat on 2009-11-26
Follow Up--
I finally got some backup software to work with the WD NSD.

Conduit will work if you use Windows type path naming convention.
i.e. 
//NSD_name/Folder_location

So far, Conduit is a bit slow.  I have yet to fully sync my music files.  But, I was in a hurry to get on the road so I cut it short.

Unison looks nice, but for the life of me, I cannot get it to work.

Anybody have any suggestions for backing up an Ubuntu laptop to a NAS?

---

### Post by madchine on 2009-12-05
Hmmm seems like some people are try to hijack the thread... As I've got the same issue (except for the brand, my NAS is a Buffalo Linkstation Live), I'll try to get it back on topic...

I've been researching this, following a suggestion from a friend. What I've come up with:

First, according to [http://en.wikipedia.org/wiki/Ethernet_crossover_cable#Automatic_crossover](http://en.wikipedia.org/wiki/Ethernet_crossover_cable#Automatic_crossover) you probably do not need a crossover cable if either of your ethernet "has the feature (automatic crossover) implemented and enabled" (i.e. is of recent date)

Second, the fairly recent network-manager option "Method: Shared to other computers" would seem to be a good match. This feature is meant to allow internet sharing but as it supposedly turns your laptop into a mini-router complete with DHCP, you should have an easy network connection to your NAS (as it's probably set up to use DHCP anyway) 

Or so my theory goes - 'cause I cannot tell in anyway if it works. I check the NAS' IP settings (DHCP) and turn it off, close down all other network options on my laptop and use 'Shared to other computers', establish a direct link with an (regular) ethernet cable and turn on the NAS. And then what?

Can anybody tell  me if this idea should work and if so, how do I know how/where to find the NAS (IP address...)?

---

### Post by frekja on 2010-09-26
For what it's worth, the method described above works for me. I'm now connected to my external drive via ethernet and to the internet via wifi at the same time.

Further detail:

I run Lucid Lynx 10.04 and connect to the internet via wireless (wlan0). I've directly connected my ethernet-based NAS (a WD Mybook World) to my local ethernet port (eth0). I'm pretty sure my ethernet card has autonegotiation as I don't have a crossover cable and it all works.

In order to make everything work, before switching the NAS on the first time, I right-clicked on the Network Manager applet, and selected 'add'. In the 'wired' tab, I added a new connection, added my local MAC address to the relevant field in the first tab (not sure that this is necessary, deselected 'connect automatically', and, in the IPv4 tab, selected 'shared to other computers'. I saved this as external-hard-drive (or whatever).

Now, just after turning my NAS on, I left click on the network manager applet, select external-hard-drive and this (I guess) sets up a DHCP server which gives an IP address to my external hard drive in the 10.42.43.x subnet. Normally I connect using samba and the netbios name of my external drive, which seems to work fine - though I found out the IP address of my external drive (for FTP, etc) by running: 'netstat --tcp -n' in the terminal.

Very easy in the end, but it took me quite a while to figure it out.

Edit: Well, somewhat easy - it turns out that 'shared to other computers' gives a dynamic IP address to my NAS, meaning that it gets a new ip address each time I use it. At this stage, I'm using 'nmap -T Aggressive -A -v 10.42.43.0/24' to find the IP address of the NAS, though I'm sure there's a better way, if only I could figure out how to assign a set IP address by MAC address.

---


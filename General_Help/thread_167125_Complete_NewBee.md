---
title: "Complete NewBee"
date: 2006-04-27
forum: General Help
---

### Post by woopie49 on 2006-04-27
Loaded Breezy onto 1 of my internal HD yesterday to try the O/S, standard installation from CD. My problem is accessing the net. I have a D-Link 504T modem/4 port router (wired) with 2 Macs connected. No problems.

Configuring the network to get on the net has me baffled as it is completely different to 10.3.9 set up. Both Macs are manually configured with my Mac set up being:

Config - manual
IP - 10.1.1.4
SB - 255.0.0.0
Router - 10.1.1.1
DNS - My IP provider servers

All the lights on the 504T are on and I can stiil access the net with the other Mac

Using DHCP does not get me access. I phoned my IP provider for some help but unfortunately they could not help me as they did not support Linux though she said she could see me connected. 

Any advice would be very much appreciated.

Thank you

---

### Post by Melciah on 2006-04-27
hi. im not sure if this will help and im also not sure if this would apply to a mac. either way, its something to try:

add this to the end of your /etc/modprobe.d/aliases

alias net-pf-10 off
alias ipv6 off

i have the exact same modem and this worked for me.

---

### Post by nanotube on 2006-04-27
can you post the output of commad "ifconfig" ?

---

### Post by woopie49 on 2006-04-28
Thanks for the replies guys, as I said complete newbee to this O/S and even command line entry. 

Only ever used Macs GUI

How to please - am also reading 

My Comprehensive Ubuntu Breezy Customization Howto

---

### Post by nanotube on 2006-04-28
hi
to find a terminal to enter commands, go to the Applications>Accessories>Terminal through the main menu that is at the top left of your screen. 
then you can enter commands in there. :)

p.s. enjoy the howto, feel free to post if you have questions.

---


---
title: "Seeking Gurus: 11.10 as HFW + VPN vs Smooth Wall + VPN vs Fire Penguin + VPN"
date: 2011-12-06
forum: General Help
---

### Post by stevennlv on 2011-12-06
Long story short: I got hacked HARD.

The whole process from FUBAR to having my digital life back has taken over a year. It's been a nightmare, and cost me a lot of money.

I got something nasty planted in to my router and it was locked in. It would trash my hardware every time I connected to it.  Even the "restore to factory default" button wouldn't kill it. It was beyond my skill level to remove.

I got new hardware = New router / Printer / USB Back Up Drive / 2 kick *** new boxes from Dell. Plus an E Reader.

I've spent the last 6-8 months upping my skill level.

I'm still primarily point and click. It's just where I'm comfortable after almost 20 years of 'doze. I'm wrapping my head around *nix fairly well. (I think.) But, I still look at Terminal as cmd prompt. I only go there if I absolutely have to.

I've recovered 100 gigs of data / games stretching back 15-20 years from multiple old system backups minus ~60MB of corrupted / infected stuff.

I've got everything up, running and working perfectly.

Heavy use of self-built, multiple, specific use VM appliances.

Insane security on the new boxes: Sandboxes / Virtualization / VMs / LGPE locked down hard / Multiple layers of complementing security software of many types / Nearly all MS network protocols disabled = No home network, etc, just what lets me get on the net / NAT Router locked down hard with lots of built in security features + using remote secure DNS resolver + lots more.  (After what I've been through...)

Next step = Hardware Firewall + VPN.

Recommendations needed please. 

I have an old 1501 that is dual boot 11.04 / XP. Primary OS is UB. XP on the other side just to get some stuff working. It will primarily be my "travel" box. [That way if I connect to a dirty public node the payload can kiss my ***! :)]

The new boxes are 7 with many UB VMs / few XP VMs. I wanted straight Ubuntu, but there were too many driver issues beyond my skill level to resolve. I would have had to write new sound drivers. (The VMs are locked down hard; almost zero communication allowed between 7 and VMs. All transfers between them occur via pen-drive. The net connection is initiated by 'doze then the VM piggybacks on NAT; no bridged connection / shared folders / shared clipboard.)

I also have an old net book that currently has a trashed / hacked / infected copy of 'doze on it.

I just used 11.10 from live USB to "crack" it and recover all the data on it.

11.10 runs PERFECT on it from live USB.

I'm going to wipe the net book and turn it in to a HFW + VPN.

But, what exactly should I put on it next?

Is there a way to turn 11.10 in to a HFW + VPN? If so that would be perfect. I'm starting to get fairly comfortable with 11.x UB and 11.10 runs all my hardware like the distro was written for this model net book. That would save a lot of potential headaches.

A few months ago, when I was getting started on this process one of the security / tech guys here recommended Smooth Wall.

One of the techs at work recommended Fire Penguin. 

I'm looking for something that is effective, primarily point and click (or at least GUI and "fill in the boxes"), has a fairly short learning curve and LOTS of documentation. It will need to work with 7 / XP / UB and VMs.

If possible I'd like something that I can maybe install a client of some kind in all of the various OSes (if that's even possible) that uses it's own network protocols to set up the VPN. (Theory being: If I use a client with its own networking protocols then I'm going to have a much smaller vulnerability foot print than if I turn all of MS's crappy / widely used networking protocols back on.) 

I'm looking to achieve a few things:

1) A HFW between me and the outside world.

2) All my boxes connect wirelessly; both at home and when I travel. I want all my "over the air" traffic encrypted from the boxes to the router so that I can't be sniffed or side-jacked (After what I've been through...) 

3) When I travel and connect to the net with UB 11.04 I want the 1501 to "call home" first and establish an encrypted connection from the public node through my router, then on to the outside world from there so that my "over the air" traffic is encrypted even on the road. (After what I've been through...) 

4) Whatever I set up will have to work with my current setup of VM's. And I'd prefer to be able to keep my router set to use a secure remote DNS resolver if that's possible?

*Which raises a question: On the new boxes w/ 7 will I have to set each UB VM to "talk" to the VPN directly so that their "over the air" traffic is encrypted as well? Or will the current setup of letting 7 handle the router connection take care of that if 7 is connected through the VPN?*

Last but not least:

5) After I figure all this out I want to set up an onion router on the 1501 / 11.04. (Yeah, I know, I'm paranoid.) I'll open a different thread on that in a few weeks. But, whatever I set up now will have to work with that as well.

Comments, suggestions, links to resources and advice all greatly appreciated.

Thanks for the help.

---

### Post by stevennlv on 2011-12-06
I've been researching, still seeking advice before I spend time and money.

This is what I'm thinking:

Belkin F5D5055 Gigabit USB 2.0 Network Adapter (works w/ 11.04 out of box according to a post on the forums)

Ubuntu 11.10? / if not then 11.04 (if adapter doesn't work w .10)

openvpn from software center (and I can get a win client for it as well)

FirewallBuilder from software center

http antivirus proxy (clam av) = "antivirus" in software center

Also wondering: Should I set this up as a server instead of a desktop. I've never built anything headless before. I'm not really sure what the difference is in the interface or if not having graphics on it would speed up the through put?

---

### Post by oldtimer7777 on 2011-12-06
Purchase a business router like this one:

[http://www.cisco.com/en/US/products/ps9928/index.html](http://www.cisco.com/en/US/products/ps9928/index.html)

It has a superior and very flexible firewall, IPS intrusion protection with sig updates..  And also really secure VPN.  I would start there, and come back when you are ready to rock and roll. If there is one thing thing that users never do, I find that it is they never purchase equipment that does what they they want, and instead rely too much on software-based to solve everything.  Just because you can run all your needs from software-based solutions, nothing beats a business router in terms of security when used also in conjunction with software-based security applications and utilities. 

> **stevennlv said:**
> Long story short: I got hacked HARD.

The whole process from FUBAR to having my digital life back has taken over a year. It's been a nightmare, and cost me a lot of money.

I got something nasty planted in to my router and it was locked in. It would trash my hardware every time I connected to it.  Even the "restore to factory default" button wouldn't kill it. It was beyond my skill level to remove.

I got new hardware = New router / Printer / USB Back Up Drive / 2 kick *** new boxes from Dell. Plus an E Reader.

I've spent the last 6-8 months upping my skill level.

I'm still primarily point and click. It's just where I'm comfortable after almost 20 years of 'doze. I'm wrapping my head around *nix fairly well. (I think.) But, I still look at Terminal as cmd prompt. I only go there if I absolutely have to.

I've recovered 100 gigs of data / games stretching back 15-20 years from multiple old system backups minus ~60MB of corrupted / infected stuff.

I've got everything up, running and working perfectly.

Heavy use of self-built, multiple, specific use VM appliances.

Insane security on the new boxes: Sandboxes / Virtualization / VMs / LGPE locked down hard / Multiple layers of complementing security software of many types / Nearly all MS network protocols disabled = No home network, etc, just what lets me get on the net / NAT Router locked down hard with lots of built in security features + using remote secure DNS resolver + lots more.  (After what I've been through...)

Next step = Hardware Firewall + VPN.

Recommendations needed please. 

I have an old 1501 that is dual boot 11.04 / XP. Primary OS is UB. XP on the other side just to get some stuff working. It will primarily be my "travel" box. [That way if I connect to a dirty public node the payload can kiss my ***! :)]

The new boxes are 7 with many UB VMs / few XP VMs. I wanted straight Ubuntu, but there were too many driver issues beyond my skill level to resolve. I would have had to write new sound drivers. (The VMs are locked down hard; almost zero communication allowed between 7 and VMs. All transfers between them occur via pen-drive. The net connection is initiated by 'doze then the VM piggybacks on NAT; no bridged connection / shared folders / shared clipboard.)

I also have an old net book that currently has a trashed / hacked / infected copy of 'doze on it.

I just used 11.10 from live USB to "crack" it and recover all the data on it.

11.10 runs PERFECT on it from live USB.

I'm going to wipe the net book and turn it in to a HFW + VPN.

But, what exactly should I put on it next?

Is there a way to turn 11.10 in to a HFW + VPN? If so that would be perfect. I'm starting to get fairly comfortable with 11.x UB and 11.10 runs all my hardware like the distro was written for this model net book. That would save a lot of potential headaches.

A few months ago, when I was getting started on this process one of the security / tech guys here recommended Smooth Wall.

One of the techs at work recommended Fire Penguin. 

I'm looking for something that is effective, primarily point and click (or at least GUI and "fill in the boxes"), has a fairly short learning curve and LOTS of documentation. It will need to work with 7 / XP / UB and VMs.

If possible I'd like something that I can maybe install a client of some kind in all of the various OSes (if that's even possible) that uses it's own network protocols to set up the VPN. (Theory being: If I use a client with its own networking protocols then I'm going to have a much smaller vulnerability foot print than if I turn all of MS's crappy / widely used networking protocols back on.) 

I'm looking to achieve a few things:

1) A HFW between me and the outside world.

2) All my boxes connect wirelessly; both at home and when I travel. I want all my "over the air" traffic encrypted from the boxes to the router so that I can't be sniffed or side-jacked (After what I've been through...) 

3) When I travel and connect to the net with UB 11.04 I want the 1501 to "call home" first and establish an encrypted connection from the public node through my router, then on to the outside world from there so that my "over the air" traffic is encrypted even on the road. (After what I've been through...) 

4) Whatever I set up will have to work with my current setup of VM's. And I'd prefer to be able to keep my router set to use a secure remote DNS resolver if that's possible?

*Which raises a question: On the new boxes w/ 7 will I have to set each UB VM to "talk" to the VPN directly so that their "over the air" traffic is encrypted as well? Or will the current setup of letting 7 handle the router connection take care of that if 7 is connected through the VPN?*

Last but not least:

5) After I figure all this out I want to set up an onion router on the 1501 / 11.04. (Yeah, I know, I'm paranoid.) I'll open a different thread on that in a few weeks. But, whatever I set up now will have to work with that as well.

Comments, suggestions, links to resources and advice all greatly appreciated.

Thanks for the help.

---


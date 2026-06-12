---
title: "2 devices in router device list"
date: 2011-09-30
forum: General Help
---

### Post by missmoondog on 2011-09-30
why are there 2 devices listed in tomato device list when using 1 computer with a wireless connection? there's the br0 and the eth1. how do i remove the br0?

i do not have anything entered in the settings for the wired connection.

thank you

---

### Post by 2F4U on 2011-09-30
I have no idea what you are talking about, but Google returned this

[http://www.dslreports.com/forum/r20682200-Tomato-What-are-br0-and-eth1-interfaces](http://www.dslreports.com/forum/r20682200-Tomato-What-are-br0-and-eth1-interfaces)
[http://en.wikibooks.org/wiki/Tomato_Firmware/Menu_Reference](http://en.wikibooks.org/wiki/Tomato_Firmware/Menu_Reference)

---

### Post by missmoondog on 2011-10-01
no idea what i'm talking about. i made it is as simple to understand as i could!!

there is a wireless device and a wired device showing up in tomato's router devices.

i DO NOT have anything wired plugged into router, other than modem obviously and vonage adapter, so what is that br0 device that's showing up?

i have wireless card setup with static ip's such as 192.168.1.104 on this machine, but i'm also seeing a 192.168.1.124, which under name says ubuntu, and today there is a third address of 192.168.1.148! i have NO computers that use those last 2 ip addresses at all.

yes, my stuff is setup securely an no one else is connecting to me.

thank you

---

### Post by Old_Grey_Wolf on 2011-10-01
br0 refers to Wired Ethernet (LAN) devices: these are connected to the router on the four Ethernet ports, either directly or via a hub or switch. **Inactive wireless devices are also moved to br0.**

> **missmoondog said:**
> yes, my stuff is setup securely an no one else is connecting to me.

It looks like something is connecting. Are you using WEP or WPA?

---

### Post by missmoondog on 2011-10-01
yes, i know what br0 refers to and as i stated i had NO wired devices connected except my vonage adapter and i know what that ip address is.

here's an image of my connections at this moment on a hard wired windows machine now. the 192.168.1.101 is this machine. the 192.168.1.15 in vonage adapter. i don't have a clue what that 192.168.1.124 ip address is, even though it says ubuntu. i statically set ALL connections whether wired or wireless and i have NOT set any to 192.168.1.124. this machine is the only one physically turned on right now also. really don't why that 192.168.1.124 is still showing up even still with all wireless systems turned off and static ip's assigned. part of why i do that is so when a system is turned off, it gets removed from tomatos  list.

i have it setup with wpa2-personal. ALL file sharing is disabled. No LAN sharing or anything!!

heck,
i just saw that there is a topic for networking and wireless. probably should've put this there. could a mod please move this there?

---

### Post by missmoondog on 2011-10-02
what ever that "extra" connection from ubuntu was is now gone, finally!

i'm on a wired laptop this morning.

---

### Post by missmoondog on 2011-10-02
on yet another computer, wireless laptop, and no extra devices showing up yet.

maybe, going to assume that what ever those devices were that were showing up, had to do with having just installed xubuntu via wubi. 

might have helped also now having disabled anything automatic on all systems such as checking for any updates and junk. hate automatic stuff going on behind my back!!

won't post back again now until something weird shows up again, and then might be only to say i've removed xubuntu if nobody knows what's going on, because if that's the case, then there must be some suspicious stuff in this things processes.

thanks

---

### Post by missmoondog on 2011-10-26
sheesh! how dumb can i be?

forgot all about auto dhcp!! that's what that "extra" ip was. it stayed in router for 24 hours (lease time) after i changed my settings to manual.

---


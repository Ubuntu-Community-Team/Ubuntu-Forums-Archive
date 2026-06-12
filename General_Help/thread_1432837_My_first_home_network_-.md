---
title: "My first home network - ?"
date: 2010-03-18
forum: General Help
---

### Post by ic2 on 2010-03-18
Hello Everybody,

I am preparing to build my very first ever home network.  I have 4 computers and I finally got the hang of using Ubuntu as a desktop and server command-line mode.

**Computer 1**
Dell has a Broadcom Gigabit Controller	= **ubuntu Gateway**

**Computer 2**
Dell has a Broadcom Gigabit Controller	= ubuntu desktop

**Computer 3**
A very old HP 800Mhz machine		= Windows XP

**Computer 4**
AMD64 has a Realtek Gigabit NIC		= ubuntu-Windows-7 dual-boot

I getting ready to purchase four extra NIC (10/100/1000baseTX).  Three will be insert into Computer 1 making it a total of four NIC in one machine, and one for my old HP machine.

Instead of buying a switch or hub, I'm planning to connect one cat-5 cable on the **Ubuntu Gateway **machine to the INTERNET, than connect the other three NICs using cat-5 cables directly to the other machines.  My question is, is this possible.  I think it should work but I never read anything about it because every one speaks of hub, switches and routers.  I rather buy the extra NICs and cables because everything is in one room on one long table, that is, if it works.  I can't wait to go to Best-Buy today :)

Thanks in advance for any help

---

### Post by lykwydchykyn on 2010-03-18
Well, for starters, if you really want to do it that way you'll need crossover cables, not regular ethernet cables.

You'll also want to get pretty familiar with iptables.  

Personally, I think for the money you're better off using a router or switch, but that's your call.  You're about to be baptized in fire getting this thing working.

---

### Post by Calash on 2010-03-18
You could do that, but the cost and maintenance of the setup would exceed a simple hub configuration with the gateway acting as the primary DHCP/Gateway.

The actual setup is a bit beyond me, but you would need 1 NIC for every computer in the gateway.  Does it have the slots to handle that many extra cards?

Assuming the hardware is not an issue I believe the setup is just a matter of configuring a DHCP server on the gateway (assuming dynamic IP's) and making sure the cards route traffic to each other.

It is more complex than it needs to be but it would be a good learning project.  Good luck with it.

---

### Post by ic2 on 2010-03-18
Thanks **lykwydchykyn**, that what I thought... use iptables to route the packet to given machine address just like a switch would.  The only difference its 3 direct connect, so gateway machine now act as a switch. I think you just spared me from being baptized in fire with the cross-cable tip.  That's should do the trick.  Unless more can be added, I think you said it all.

Hello **Calash**, Yes, it has 4 regular PCI slots.  I hope I don't need PCI-e.  I thinks those are for 10 gigabit and/or Fiber Optic use.  I just started this spring semester taking a network+ course.  I think I'll learn more by hands-on experience than remembering all of those standards that is not getting me anywhere fast.  That's why I really want to try it this way.

---

### Post by wrose51106 on 2010-03-18
Let me throw my 2 cents in here also. 

First off, congrats on bettering yourself with education and wanting to take away the most information you can.

Second, I agree with the others. I would hit up Newegg and get a cheap switch. Take the PC you planned on putting the NIC's in and install IPCOP or another variation and learn that way.

Again only my opinion, best of luck in whichever way you decide!

-Bill

---

### Post by ratcheer on 2010-03-18
To the OP, I do not think you would like that setup at all.

You simply need to add a gigabit ethernet switch between your router or gateway machine and all the other machines. That would give you a consistent, maintainable LAN. Gigabit switches are cheap, too. I bought an 8-port Netgear about a year ago for $80, new at a retail store.

My network layout is that my DSL modem is my router and DHCP server. It connects to the gigabit switch. Then, also connected to the switch are three computers and a dual-band wireless N router that I reconfigured to act as a simple wireless access point. A Macbook Pro, a PS3, a PSP, and a Wii all connect wirelessly. Everything works steadily and with no configuration hassles. It would be a nightmare without the switch.

I hope this helps.

Tim

---

### Post by ic2 on 2010-03-18
Yes, Calash, it was quite an learning experience and yes lykwydchykyn, I felt the heat rising before getting to the good parts. I'm so glad I asked before making that move to Best-Buy because I took both you guys comment into consideration, than I started ripping out extra cards from my other machines than found in the basement, Now I learn the systems itself (most BIOS) only allow for two Ethernet cards.  That's why we always read one in and one out.  I think it still can be done because you can change the IRQ number but who want to do that forever and that is not going to get anyone a job in the field so I'll get a SWITCH since coming back to read wrose51106 post, than ratcheer broke the law down.  I'll be modeling all my efforts behind that.  What a GREAT forum.  You guys save a life time of wondering, Now I can use that money to buy my girl friend that new dress been bugging me about.  Thanks for being there guys.  Hope to hear more about custom set-ups.  I'm going downtown now to get one gigabit card and some cat-49 cables  :)  , wireless will be next. For now my Ubuntu Gateway is all about a very secure firewall.  I'm tired of getting bugs *or whatever I been seeing *every other month or two under Windows-XP and now Windows-7 tooooo and I saw it happen with Fedora.  So now it's more about Arch-Linux and UUbuntu for me.

So it's ok to let DSL be the router, etc.  I use DSL too.

Thanks again

---

### Post by Iowan on 2010-03-18
> **ic2 said:**
> So it's ok to let DSL be the router, etc.  I use DSL too. My DSL modem feeds a switch - into which the rest of my computers connect - even the server I use for  DHCP/DNS (although my modem is capable of DHCP as well as firewalling and NATing).

---


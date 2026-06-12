---
title: "Do I need a router?"
date: 2006-03-15
forum: General Help
---

### Post by TheFr00n on 2006-03-15
Hi there

I've searched extensively on these boards and have figured out most of my problem, but I still have some questions I'm hoping someone can help me with.

The main computer in my house is a desktop PC running Ubuntu 5.10. I have succeeded in weaning the inhabitants off the crappy ME install that the system dualboots to (yay!).

The system has no network card, but connects to the internet via an ADSL broadband USB modem.

Now, there will soon be arriving two shiny new laptops to live in our house. I want the PC to remain as the internet connection, and share it wirelessly with the laptops.

My question is, do I need a wireless router to do this? Or can I get away with just getting a wireless network card for the machine?

Further, I have read conflicting reports that a USB router will interfere with the functioning of a USB broadband modem, and that I should consider a combined router/modem device instead.

Any thoughts?

Thanks,
D

---

### Post by mips on 2006-03-15
What you propose is possible. You basically want turn your PC into a router / wireless access point.

In order for this to work it means the PC will have to be online at all times else the laptops wont work. It will also mean some configuration on your part getting the wireless card to work as an access point.

I personally would not go this route. I would rather a buy a all-in-one modem/router/firewall/4port switch/wireless access point to do the job (Linksys,Netgear,Billion product). It can stay on 24/7/365 and my clients wont be dependant on the pc and the setup will most likely be much easier.

---

### Post by TheFr00n on 2006-03-15
Hi Mips
  Thanks for the input.
  
  The machine does stay on 24hrs a day anyway. I was planning to use FireStarter to configure my system to use my existing modem for teh intarwebs, and share it via the wireless card.

  What I haven't succesfully understood yet is why a combined router/modem product is superior to this. It's certainly more expensive.

  Is it purely because of complexity? Or are there genuine benefits to owning one? If I understand you correctly, I think you're saying that if I own a router, then the PC doesn't necessarily need to be switched on.

---

### Post by JustRandomName on 2006-03-15
Yes, the main advantage is that the PC doesn't have to be turned on.

There is usually a lot of hassle in doing what you propose, a router would come with a helpful web-based configuration.

Getting a router will also free up your gateway PC, I am sure you will be able to find a good use for it.

You can pick up routers these days for £20-£40 . This will eventually save you hours of work, so you work out how much your time is worth.

---

### Post by macerata on 2006-03-15
Wireless routers are excellent.  I can easily recommend the Netgear DG834GT - it's easy to set up and maintain, it's got an internal modem and firewall, and is pretty cheap.

---

### Post by mips on 2006-03-15
[QUOTE=TheFr00n]Hi Mips
  Thanks for the input.
  
  The machine does stay on 24hrs a day anyway. I was planning to use FireStarter to configure my system to use my existing modem for teh intarwebs, and share it via the wireless card.

  What I haven't succesfully understood yet is why a combined router/modem product is superior to this. It's certainly more expensive.

  Is it purely because of complexity? Or are there genuine benefits to owning one? If I understand you correctly, I think you're saying that if I own a router, then the PC doesn't necessarily need to be switched on.[/QUOTE]

My reasoning is to go for the simplistic option which results in less frowning and pulling of hair ;)

Alternatively you can still use that PC as a firewall/nat router. plug an additional LAN card into it and connect a wireless router to it.

There are many ways to skin a cat and I prefer the easy way. The choice is ultimately yours to make. It would be a fun experiment to do I must admit and if I was to do it I would rather use OpenBSD/FreeBSD for this function. 

**If you do go the PC + wireless card route please just research beforehand which card works & whether it will work in AP mode.** You will also have to implement WPA for security.

This would be a good start [http://www.ubuntuforums.org/showthread.php?t=111972](http://www.ubuntuforums.org/showthread.php?t=111972)

---

### Post by JustRandomName on 2006-03-16
> Wireless routers are excellent. I can easily recommend the Netgear DG834GT - it's easy to set up and maintain, it's got an internal modem and firewall, and is pretty cheap.

That router is excellent, and NETGEAR used open-source products so the source code is available.

Search google to find modified versions of the source adding loads of extra features that you usally pay £££'s for.

---


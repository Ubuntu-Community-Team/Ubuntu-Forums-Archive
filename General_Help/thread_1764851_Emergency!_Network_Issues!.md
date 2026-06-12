---
title: "Emergency! Network Issues!"
date: 2011-05-22
forum: General Help
---

### Post by dh04000 on 2011-05-22
Ok, I'm really hoping that a artrustic member of the forums reads this becuase I need help, and unfornately, I need it fast. I'm visiting my parents residence from grad school, where I live 3 hours away.

My parents computer was "down", so I've been trying to fix it. Turns out that the video card had burned up, so I took one out their cera 2001 computer and put it in their 2006 one. Worked like a charm, we can see video again.

Finally I could see if it was "actually" working, and it turns out the networking it out too. They have dsl internet, and it does not detect either the usb or ethernt plug being placed in the computer. In fact, it doesn't detect anything at all network wise. I'm not sure if it detects it own card. Unfornately, this is my last day here before I have to god home. So I need help quick.

I need some dianosis to see whats wrong, and I need advice to fix it. The advice has to be easy enough that if I'm not here, they can fix it on their own. replacing networking cards by hands is beyound them, so the solution would have to be a plug-in usb device. Do they make those?

Their computer has windows xp hom and ubuntu 10.04 (installed for these kinda problems for diagnostics).

Please help!

---

### Post by dh04000 on 2011-05-22
Ok, I'm really hoping that a artrustic member of the forums reads this becuase I need help, and unfornately, I need it fast. I'm visiting my parents residence from grad school, where I live 3 hours away.

My parents computer was "down", so I've been trying to fix it. Turns out that the video card had burned up, so I took one out their cera 2001 computer and put it in their 2006 one. Worked like a charm, we can see video again.

Finally I could see if it was "actually" working, and it turns out the networking it out too. They have dsl internet, and it does not detect either the usb or ethernt plug being placed in the computer. In fact, it doesn't detect anything at all network wise. I'm not sure if it detects it own card. Unfornately, this is my last day here before I have to god home. So I need help quick.

I need some dianosis to see whats wrong, and I need advice to fix it. The advice has to be easy enough that if I'm not here, they can fix it on their own. replacing networking cards by hands is beyound them, so the solution would have to be a plug-in usb device. Do they make those?

Their computer has windows xp hom and ubuntu 10.04 (installed for these kinda problems for diagnostics).

Please help!

EDIT: Meant to hit ubuntu, not kubuntu as prefix.

---

### Post by dandnsmith on 2011-05-22
**ifconfig** should show if the ethernet interface has been found (or use ipconfig in XP)

I'm not sure about the usb bit - is this an alternative connection method to your router? If so, perhaps it's the router that is the problem.

---

### Post by Wim Sturkenboom on 2011-05-22
lshw, lspci, lsusb and dmesg are some commands to see what is at least reconized / available.

If you have your PC with you, try it with the modem. Else take it to the neighbours and see what happens when you hook it up to their PC. I would suspect a power spike or lightning damage which might well have fried a whole lot of stuff.

Your parents can take the modem to the ISP as well (if it's in town) and let them test it.

Leaves you to figure out if the network card / usb ports on the PC are still functional (memory stick, external HD will do for USB).

---

### Post by overdrank on 2011-05-22
Threads merged :)

---

### Post by charm_quark on 2011-05-22
> **Wim Sturkenboom said:**
> lshw, lspci, lsusb and dmesg are some commands to see what is at least reconized / available.

If you have your PC with you, try it with the modem. Else take it to the neighbours and see what happens when you hook it up to their PC. I would suspect a power spike or lightning damage which might well have fried a whole lot of stuff.

Your parents can take the modem to the ISP as well (if it's in town) and let them test it.

Leaves you to figure out if the network card / usb ports on the PC are still functional (memory stick, external HD will do for USB).

very sound advice

1) check modem
2) check motherboard / network card.

---

### Post by dh04000 on 2011-05-22
> **dandnsmith said:**
> **ifconfig** should show if the ethernet interface has been found (or use ipconfig in XP)

I'm not sure about the usb bit - is this an alternative connection method to your router? If so, perhaps it's the router that is the problem.

The dsl modem can connect to a computer via, wireless, thernet, or usb.

The wireless, ethernet, and usb work on any computer but my parents. I ran your command, and only got

etho    Link encap: Ethernet  HWaddr (some numbers)
        UP Broadcast Multicast  MTU:1500  Metric:1
        Bunch of other stuff

lo      Link encap: Local Loopback
        (some ip address and mask)
        Bunch of Stuff

---

### Post by dh04000 on 2011-05-22
> **Wim Sturkenboom said:**
> lshw, lspci, lsusb and dmesg are some commands to see what is at least reconized / available.

If you have your PC with you, try it with the modem. Else take it to the neighbours and see what happens when you hook it up to their PC. I would suspect a power spike or lightning damage which might well have fried a whole lot of stuff.

Your parents can take the modem to the ISP as well (if it's in town) and let them test it.

Leaves you to figure out if the network card / usb ports on the PC are still functional (memory stick, external HD will do for USB).

Usb devices still work. I'm using a usb mouse with it right now.

I ran lshw, and under network, I got

description: Ethernet interface
product: 82562EZ 10/100 Ethernet Controller
vender: Intel Corporation
bus info: pci (numbers)
tons of other stuff, not that useful

So it DOES detect a network card, but not any connections?

---

### Post by dandnsmith on 2011-05-22
That seems to be the inference - but you really needed to post IP addresses for the interfaces, and possibly traffic figures to be sure.

I'd certainly look very hard at the modem now.

---

### Post by dh04000 on 2011-05-22
> **dandnsmith said:**
> That seems to be the inference - but you really needed to post IP addresses for the interfaces, and possibly traffic figures to be sure.

I'd certainly look very hard at the modem now.

Why would the dsl modem by the problem if it works with any other computer but my parents?

Doesn't this point at the network card in their computer?

Also, if this were the case, would buying a usb wireless adapter fix the problem?


EDIT: as a secondary note which I'm not sure matters, the usb ports on thier computer likes to freak out if more than one device per usb node is plugged in. Complains of power issue, I have all devices plugged on different usb nodes.

---

### Post by Wim Sturkenboom on 2011-05-22
Does the modem function as a router as well? If so, is the mac address / are the mac addresses of your parents PC blocked in the router?

You mention other PCs; whose PCs are those?

USB ports in the front of a PC often can not provide sufficient power. So only those at the back are usefull for devices that draw high currents. And don't use USB extension leads with them.

---

### Post by dh04000 on 2011-05-23
I ran to bestbuy and bought a new network card for their desktop, and now its working.

Thanks for the help.

---


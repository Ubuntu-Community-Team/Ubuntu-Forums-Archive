---
title: "Wireless problem on start up"
date: 2011-11-18
forum: General Help
---

### Post by dimitars on 2011-11-18
Hello guys,
I have problem with my Ubuntu 11.10. When i boot my machine i almost always have problem connecting to my wireless network. It just tries to connect but no success. Sometimes it asks me for the wireless password even though i have it remembered in wireless settings. 
Generally i solve this with trying to connect to other network than disconnect than connect to my network again. This sometimes work, but more often not. Then i try to go in my wireless settings and just poke around in the settings(unchecking autoconnect, rewritting the password, and then saving). After some time sometimes it connects. 
If any of the previous methods fails, i log out and log in to my account and that sometimes helps.

So this happens almost always(every 99 times out of 100), and i do this stuff and takes me up to 10 minutes to manage to connect. 

So do you have any solution? 
I would have posted more information about my network and what not but I am novice in ubuntu, so i don't know any terminal commands and other "hacks" to show you my info. If you need more info just tell me what you need and how to obtain it.

---

### Post by Roasted on 2011-11-18
Run "lspci" in terminal. Look for an entry about "ethernet controller." It's likely you'll have two... wired and wireless. Post the wireless one here. It'll show us exactly what wireless card you have.

Also, tell us about your network. Is this a home network? Work network? Basic Linksys router or a full blown Cisco controller? Does it happen everywhere? Can you duplicate it even at a Starbucks or McDonalds wifi, friend's wireless network, etc.?

---

### Post by dimitars on 2011-11-20
```
01:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe (rev 01)
02:00.0 Network controller: Broadcom Corporation BCM43225 802.11b/g/n (rev 01)

```

It is happening again at my friends house too.

---

### Post by Miljet on 2011-11-20
If you have an Acer machine this link may help.
[http://ubuntuforums.org/showthread.php?t=1704122](http://ubuntuforums.org/showthread.php?t=1704122)

If not, do a Google search for "Broadcom BCM43225 Ubuntu". There are hundreds of threads addressing problems with Broadcon wireless chipsets.

Wish I could give you a more definitive answer.

---


---
title: "Kubuntu + Internal Laptop Wifi?"
date: 2006-04-20
forum: General Help
---

### Post by rnaodm on 2006-04-20
Ive searched for a while with no luck. Im on an Inspiron 1300 with internal wifi trying to use wifi-radar but it finds no wireless connections and I know there are three available. Do I need a USB/PCMCIA access point or are there drivers on onboard wifi?

---

### Post by nanotube on 2006-04-21
what is the make/model of your internal wireless card?

i have a dell inspiron 5150 with intel 2200bg internal wifi card, and it works without a problem... 

search around these forums (or google) for your wifi card, and you may come up with an answer to your problem.

---

### Post by electronate on 2006-05-20
Toshiba Tecra S2, Kubuntu Breezy 5.10...  

I tried the Synaptic install of wireless stuffs: ipw2200...

Ended up following a 3 step install after googling ubuntu wireless.

i think u might have some luck with apt-get install, and the following packages in respective order:

802... something
ipw2200-<version>
ipw2200-fw-<version>

I think this worked, I can pick up wireless traffic and use airsnort which is fun.   I haven't got a wireless network of my own setup and have not completely connected and visited websites or the like...

---


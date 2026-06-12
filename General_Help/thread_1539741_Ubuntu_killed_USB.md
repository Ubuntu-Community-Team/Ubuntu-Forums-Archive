---
title: "Ubuntu killed USB"
date: 2010-07-26
forum: General Help
---

### Post by Brannyh on 2010-07-26
Ok, I just loaded a USB drive with music from iTunes on my mac, ejected it properly, plugged it in to my Ubuntu dell dimension 3000 and it came up on the desk top but while i was browsing it it died! I tested it on two other computers, its dead, the light wont even light up! it is a DANE-ELEC 2 GB.

---

### Post by aidenscool09 on 2010-07-26
Well, it died then didn't it. It's nothing to do with your operating system weather it dies or not. It could be temporary. And are you sure you had it plugged in properly when you first put it in? The power connection might have shorted out. Also try a different USB port.

---

### Post by Nick_Jinn on 2010-07-26
Try using Gparted and see if reformatting it helps. Gparted might recognize it even if it doesnt mount.

If not then its really dead. You can probably get it replaced if its still in warranty....if not, then its old and storage devices dont last forever.



I know Karmic had problems with spinning down hard disks due to power saving mode, but there are no moving parts in a USB drive so I dont think its possible for Ubuntu to damage the actual hardware.....try reformatting it.

---

### Post by Brannyh on 2010-07-26
I tried it on all ports and on 2 computers! I am suspicious because it died AS i was browsing it

---

### Post by cj.surrusco on 2010-07-26
USB flash drives only last for a certain amount of read/write cycles, so it might have reached it's limit. Check if you can still see it in GParted, though. If you can, you might be able to reformat it.

---

### Post by Brannyh on 2010-07-26
Is gparted in the command line?

---

### Post by aidenscool09 on 2010-07-26
Hey CJ, nice job on the Crucial Ballistix. Probably the best RAM money can buy. But DDR2 1066MHz is better though.

---

### Post by aidenscool09 on 2010-07-26
Nah, but you have to open it as root. If you want to open it thought terminal, do
```
gksudo gparted
```

---

### Post by Brannyh on 2010-07-26
I waited a couple of minutes and tried again and it worked but then it also died while browsing again so i will try gparted! Thanks!

---

### Post by aidenscool09 on 2010-07-26
Might be a bad connection in your USB stick then.

---

### Post by Brannyh on 2010-07-26
gparted did not detect it, only the hard drive so i guess i will just get a new one.. it was only 2 GB

---

### Post by aidenscool09 on 2010-07-26
Actually, does the USB stick get hot at all? Mine gets really hot sometimes (probably because it's been through the washing machine and tumble drier several times) but it's never given up on me.

---

### Post by Brannyh on 2010-07-26
It doesnt get hot but its like got a big piece of plastic around it so I cant really tell, but i replugged it in AGAIN and gparted detected it but i think there is something wrong with the USB so i will just get a new one! Thanks for all your help!

---

### Post by aidenscool09 on 2010-07-26
Sounds like you got a dodgy drive. And how long ago roughly did you buy it?

---

### Post by Brannyh on 2010-07-26
About a year ago

---

### Post by aidenscool09 on 2010-07-27
Ah, well thats a while, i've had my trusty San Disk Cruzer for several years now, still working perfectly. But i would say it's a dodgy connection between the USB stick and the USB port. Have a look at the little gold pins (plates) on the USB stick where you put it in and look if there is any sign of wear on them.

---

### Post by cj.surrusco on 2010-07-27
> **aidenscool09 said:**
> Hey CJ, nice job on the Crucial Ballistix. Probably the best RAM money can buy. But DDR2 1066MHz is better though.

Hah! How is that? DDR3 is faster, and mine is running at 1333HHz!

---

### Post by aidenscool09 on 2010-07-27
Well, DDR3 carries out more processes than DDR2 so actually i guess it would be about the same. DDR3 just has more functions than DDR2 so DDR3 is more stable but DDR2 is still fast but less expensive. Oh well, either way, Crucial BallistiX is the way to go.

---

### Post by Nick_Jinn on 2010-07-27
I thought.....that they all had their own clock speeds so one isnt inherently faster than the other, but maybe the upper maximums are.....However, DDR3 has more latency, which translates into more drag and to the user experience is 'slower' for quick small applications. I would take 6gb of the fastest DDR1 if I could, but they dont really make high end DDR1 and whats left is really expensive and doesnt work in modern motherboards.

---

### Post by Brannyh on 2010-07-29
Arent we slightly off topic?

---

### Post by cj.surrusco on 2010-07-29
> **Brannyh said:**
> Arent we slightly off topic?

No, we're still talking about computers ;)

---


---
title: "virtualization on ubuntu? how fast?"
date: 2009-09-03
forum: General Help
---

### Post by serious7 on 2009-09-03
Hey I am about to start studies in unviersity and my university has msdn connections which will give me free download of windows 7 64 bit. I am running ubuntu 64 bit on a reiserf partition. How fast is it to virtualise windows 7 on ubuntu? I have never attempted virtualization before and it would be helpful to know how well it would perform? I am willing to delete all existing partitions of windows in my machine and just virtualize it if it works well. Like can it run direct x 10 games on virtualization? 

I have i7-920 gtx 280/ 6 gb ddr3 on my computer so hopefuly it would run fast. What do you guys think?

---

### Post by stefangr1 on 2009-09-03
I tried the Windows-7 beta in vmware, and it was very, very slow compared to other operating systems (could be due to it's beta status). On a processor with full virtualization support there's suppozed to be a 7% penalty, but hard disk performance is really bad in vmware, even when a vm is on a separate disk.

---

### Post by NoaHall on 2009-09-03
Virtualbox (from the official site, not the OSE) works the best out of all virutal machines, and if you give about 3gb to it, it'll run pretty fast (mine does, I give it about 4 gb, and 128mb video ram)

---

### Post by serious7 on 2009-09-03
well I dont want to pay for virtualization...so I will rely on synaptic to get virtualbox or something equivalent. Were you guys able to play games on windows 7 virtualization in ubuntu? Does my processor have virtualization support?

---

### Post by NoaHall on 2009-09-03
You don't have to pay for virtualbox on the site, it's free. The synaptic one sucks. Don't use it.

Your processor does support it - but it depends on your motherboard. It might not support it (but you'll still be able to run VM's pretty fast)

---

### Post by Whiffle on 2009-09-03
> **serious7 said:**
> well I dont want to pay for virtualization...so I will rely on synaptic to get virtualbox or something equivalent. Were you guys able to play games on windows 7 virtualization in ubuntu? Does my processor have virtualization support?

Its still free from the virtualbox site, it just has some "non-free" (aka, proprietary) stuff in it that you won't get through the ubuntu repos.

My C2D e8400 has virtualization, I would be very very very surprised if an i7 didn't.  

Overall it runs almost as fast if not as fast as it does natively, although I think graphics support for games is still primitive.

---

### Post by serious7 on 2009-09-03
> **NoaHall said:**
> You don't have to pay for virtualbox on the site, it's free. The synaptic one sucks. Don't use it.

Your processor does support it - but it depends on your motherboard. It might not support it (but you'll still be able to run VM's pretty fast)

I use evga x57 tri sli mother board (but im only using one gpu).
does it support virtualization?

> "Its still free from the virtualbox site, it just has some "non-free" (aka, proprietary) stuff in it that you won't get through the ubuntu repos.

My C2D e8400 has virtualization, I would be very very very surprised if an i7 didn't. 

Overall it runs almost as fast if not as fast as it does natively, although I think graphics support for games is still primitive. "

Why doesnt games work on virtualization? The only reason why i need windows 7 is for games....!?

---

### Post by NoaHall on 2009-09-03
Games DO work, but not like they would in a real Windows install -  however, they can work very well in my experience.

I can't find any details/specs for your motherboard, but if you go into your bios settings, it will tell you.

---

### Post by serious7 on 2009-09-03
> **NoaHall said:**
> Games DO work, but not like they would in a real Windows install -  however, they can work very well in my experience.

I can't find any details/specs for your motherboard, but if you go into your bios settings, it will tell you.

Do games perform better on virtualization than using wine?

---

### Post by Bear Knuckle on 2009-09-03
> **serious7 said:**
> I use evga x57 tri sli mother board (but im only using one gpu).
does it support virtualization?

It's the processor, which may support virtualization by some special instructions. What processor do you have?

> 
Why doesnt games work on virtualization? The only reason why i need windows 7 is for games....!?

Virtualising a graphicscard with full support is a task, no vendor of virtualization software has put much effort in yet. I guess the some reason for this are the closed source drivers of the graphicscards manufacturers and the complexity of APIs like Direct X.

And, the most important point, as the word "virtualization" tells it, the hardware is only virtual, but for efficient gaming you need direct hardware support, which is in contrary to the concept of virtualization in software. It's just not fast enough!

---

### Post by NoaHall on 2009-09-03
Yes, they run better on VirtualBox than on wine (most of the time). 
However, some games will need wine to run it well(to do with the graphics).

I think , with your motherboard, it will be fine using virutalisation.

Bear Knuckle: It depends on the motherboard - it must support virtualisation boosting)

---

### Post by P4man on 2009-09-03
a virtual machine virtualizes everything, including the videocard. In the case of virtualbox, this is a 15 year old non 3D SiS  videocard. Can you play games on it? Sure, solitaire and pacman. Pretty much nothing else.

---

### Post by NoaHall on 2009-09-03
I can run quite a few games after installing guest additions (on windows 7).

Half life 2, rome total war, etc, however, it won't run the newest games.

---

### Post by serious7 on 2009-09-03
> **NoaHall said:**
> I can run quite a few games after installing guest additions (on windows 7).

Half life 2, rome total war, etc, however, it won't run the newest games.

mhm....how much space do you guys recomend to virtualize windows 7 on ubuntu?

---

### Post by NoaHall on 2009-09-03
I've given mine 100 GB - although I use it a lot for abode software and as I manage several sites, I need the space (saving files to disk)

Min would be around 20GB I would say, but I would give it around 50GB on the safe side.

---

### Post by Bradj47 on 2009-09-03
I highly un-advise the use of VirtualBox for games. Everyone I've talked to and I have all had problems with things going into fullscreen on VirtualBox. We even have trouble with maximized windows. Especially Win7. XP is the only type of Windows I've seen run normally on VirtualBox. For me Windows runs much better on It's own partition.

---

### Post by Slim Odds on 2009-09-03
> **Bear Knuckle said:**
> And, the most important point, as the word "virtualization" tells it, the hardware is only virtual, but for efficient gaming you need direct hardware support, which is in contrary to the concept of virtualization in software. It's just not fast enough!

LOL 

This is exactly why "they haven't put much effort into it".

Why should they? If you really need the advanced graphics capabilities, you need direct access to the graphics hardware. So why would they waste their time?

---

### Post by serious7 on 2009-09-03
> **Bradj47 said:**
> I highly un-advise the use of VirtualBox for games. Everyone I've talked to and I have all had problems with things going into fullscreen on VirtualBox. We even have trouble with maximized windows. Especially Win7. XP is the only type of Windows I've seen run normally on VirtualBox. For me Windows runs much better on It's own partition.

I  want to use ubuntu but I'm spending most of my time on the windows environment just because. It would be a hell alot easier for me to transition into the linux environment if I have windows 7 virtualized. I've been using windows since 3.1 and I love the potential of linux (I just started linux very recently). However, I just cant stay on the operating system 24/7 because i'm USED to using windows. If i can virtualize windows 7 to the point that it will run everything except games properly, I will definitely spend most of my time on ubuntu. Therefore, I will naturally grow accustumed to ubuntu XD. I'm sick of rebooting the computer just because I want to use a program or two that doesnt work on linux (photoshop cs4 etc).

---

### Post by Slim Odds on 2009-09-03
> **serious7 said:**
> If i can virtualize windows 7 to the point that it will run everything except games properly, I will definitely spend most of my time on ubuntu.

Should not be a problem at all.....

I have an XP virtual machine for "special occasions", lol

Go for it....

---

### Post by Bear Knuckle on 2009-09-04
> **Slim Odds said:**
> LOL 

This is exactly why "they haven't put much effort into it".

Why should they? If you really need the advanced graphics capabilities, you need direct access to the graphics hardware. So why would they waste their time?

You got it. :-)

Question: I thought the processor has some special instructions used for virtualization. What has the motherboard to do with it?

---

### Post by NoaHall on 2009-09-04
The motherboard has to be able to support it (for a boost) or else, it's just like not having it at all.

---

### Post by jocko on 2009-09-04
> **Bear Knuckle said:**
> You got it. :-)

Question: I thought the processor has some special instructions used for virtualization. What has the motherboard to do with it?
Even if hardware virtualization is built in to the cpu, it has to be turned on in the bios. Some motherboard and laptop manufacturers turn off virtualization support in the bios, and either hide or completely remove the option to activate it again. Other manufacturers leave the option easily accessible in the bios setup. So you need to look in your bios, and if you can't find the option, try to find out if it's possible to unhide any hidden options in your bios (by pressing a specific key combination while in the bios setup. This should be in your motherboard manual).

---

### Post by Bear Knuckle on 2009-09-04
Do you have a source where I can inform myself about virtualization support of motherboards?

---

### Post by jocko on 2009-09-04
> **Bear Knuckle said:**
> Do you have a source where I can inform myself about virtualization support of motherboards?
Your motherboard manual can probably be found on the manufacturers website.

---


---
title: "Is my PC 64 bit?"
date: 2011-09-16
forum: General Help
---

### Post by kyral210 on 2011-09-16
I have an AMD Athlon 64 X2 and I always thought it was a 32 bit chip. I ran Belaric Advisor and it says that my chip is 64 bit ready. What does that mean? Is that it is a full 64 bit chip or is it I CAN run 64 bit architecture but its not advisable? I am running Windows 7 Pro 32 bit.

Also, if I do have a 64 bit chip, can I run Ubuntu 64 bit alongside Windows 7 32 bit?

---

### Post by realzippy on 2011-09-16
Yes,real 64 bit CPU and yes you can.

:)

---

### Post by kyral210 on 2011-09-16
I bought 32 bit Windows and I should have got 64! Hmmm. If I got a windows 7 'upgrade' DVD which is 64 bit would that turn my machine into a 64 bit machine or can you only upgrade from 32 to 32?

Also, can I duel boot 32 bit windows and 64 bit Ubuntu?

---

### Post by hansdown on 2011-09-16
Hi, kyral210.

You should probably get a 64bit install disk.

Then you can install 64bit linux, along side.

32bit linux will install beside both.

---

### Post by realzippy on 2011-09-16
> **kyral210 said:**
> BOLLOCKS! I bought 32 bit Windows and I should have got 64! 

If you do not have more than 4 GB RAM,you have no advantage in running
64 bit..

---

### Post by mips on 2011-09-16
> **kyral210 said:**
> I have an AMD Athlon **[COLOR="Red"]64[/COLOR]** X2...

What does that mean? Is that it is a full 64 bit chip or is it I CAN run 64 bit architecture but its not advisable?


Also, if I do have a 64 bit chip, can I run Ubuntu 64 bit alongside Windows 7 32 bit?


You think they called it AMD 64 because it's 32-bit?

It's 64-bit, it can run a 64-bit OS.

Yes, not a problem.

---

### Post by hansdown on 2011-09-16
> **realzippy said:**
> If you do not have more than 4 GB RAM,you have no advantage in running
64 bit..

Good point, realzippy.

---

### Post by mips on 2011-09-16
> **realzippy said:**
> If you do not have more than 4 GB RAM,you have no advantage in running
64 bit..

Nah, things like audio & video encoding are much faster in 64-bit, same goes for handling compression/archives even if you have less than 4GB ram.

---

### Post by Paqman on 2011-09-16
> **mips said:**
> Nah, things like audio & video encoding are much faster in 64-bit, same goes for handling compression/archives even if you have less than 4GB ram.

^This. The main reason I've been running 64-bit for years is speed, not RAM. Why throttle your chip down if it's 64-bit?

---

### Post by kyral210 on 2011-09-16
I have installed 64 Bit Ubuntu (11.04) on my machine, but just like the last time I tried to duel boot, GRUB craped out and wont load the OS after I ran the updates. I HATE GRUB!!!!

---

### Post by NightwishFan on 2011-09-16
Grub is no different between 32 and 64-bit. What do you specifically mean by 'won't load'?

---

### Post by MasterNetra on 2011-09-16
If your ram is less then 2GB don't bother with Window 7 64bit, the min req for 64bit version of windows 7 is 2GB.

> **Paqman said:**
> ^This. The main reason I've been running 64-bit for years is speed, not RAM. Why throttle your chip down if it's 64-bit?

Resource consumption. My processor for example is 64bit, but I only have 1GB of ram. A 64bit of Windows 7 will not run well or at least I won't have much leftover for anything else. Its really best (if you do resource intensive stuff) to not do 64bit with anything less then 4GB of ram or 2GB of ram if your just a casual user.

---

### Post by FuturePilot on 2011-09-16
> **realzippy said:**
> If you do not have more than 4 GB RAM,you have no advantage in running
64 bit..

Not true. I ran 64 bit Ubuntu on a laptop with 2 GB of RAM with no problem. There is a noticeable speed difference with 64 bit.

---

### Post by haqking on 2011-09-16
> **realzippy said:**
> If you do not have more than 4 GB RAM,you have no advantage in running
64 bit..

x64 will allow you to use and see the extra ram if you dont want or have PAE 32 bit, but you will still get a performance increase with less

---

### Post by SavageWolf on 2011-09-16
If you have 64 bit stuff and it works, there is no point to NOT using it, is there?

---

### Post by philinux on 2011-09-16
Moved to General Help forum.

---

### Post by MasterNetra on 2011-09-16
> **SavageWolf said:**
> If you have 64 bit stuff and it works, there is no point to NOT using it, is there?

If you have less then 2GB of ram there is. Ram Usage is increased with 64bit and not slightly mind you. Again your fine if have 2GB of ram or more. For me its not ideal as I only have 1GB of ram. And 64bit Ubuntu idles at around half of my ram.

---

### Post by blueridgedog on 2011-09-16
I generally run 64 bit for the increased processor speed and absent some older systems or really limited hardware think that it should be the default.

---

### Post by NightwishFan on 2011-09-16
I have a Pentium 4 computer running Debian 64-bit and it works great. It uses around 150mb of ram on startup (gnome). Ubuntu or Debian just disable some un-needed services. They get pushed to swap if you need more ram any-way but it helps to not have those page faults every once in a while. :)

---

### Post by Topsiho on 2011-09-16
Your processor is not only 64 bits (which means that data are processed in chunks of 64 bits at a time), but has also 2 cores, meaning that it really is a double processor.

A 64 bit processor can handle internal memory that's more than 4 GB, which is also nice to know.

Topsiho

---

### Post by oldos2er on 2011-09-16
> **realzippy said:**
> If you do not have more than 4 GB RAM,you have no advantage in running
64 bit..

Unless you run tasks such as video encoding, which are demonstrably faster.

---

### Post by oldos2er on 2011-09-16
> **SavageWolf said:**
> If you have 64 bit stuff and it works, there is no point to NOT using it, is there?

Unless you have some unusual hardware that only has 32-bit Linux drivers, no.

---

### Post by SavageWolf on 2011-09-16
> **oldos2er said:**
> Unless you have some unusual hardware that only has 32-bit Linux drivers, no.

I did say "if it works", didn't I?

---

### Post by kyral210 on 2011-09-26
Running Ubuntu 64 bit now, like it!

---

### Post by haqking on 2011-09-26
> **kyral210 said:**
> Running Ubuntu 64 bit now, like it!

cool, have fun.

Dont forget to use thread tools to mark the thread as solved.

Cheers

---


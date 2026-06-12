---
title: "Anyone got a PCI to IDE controller working on 9.10"
date: 2010-04-07
forum: General Help
---

### Post by teejcee on 2010-04-07
I guess the title says it all.

I'm trying to find a reasonably priced PCI to IDE controller that will work under Karmic. I have just built up a new PC which has SATA HDDs and want to put my old IDE drives in it. It has only one IDE interface on the mobo which I've got my DVD/CD drive on.

My research so far has found users have tried in the past with varying success.

Any input would be appreciated.

Cheers,
TC

---

### Post by teejcee on 2010-04-21
Bump....

---

### Post by srs5694 on 2010-04-21
PATA (aka IDE) supports two devices per chain, so you should be able to connect your PATA hard disk to the same connector as you're using for the DVD drive, provided the cable and mounting locations are suitable from a physical point of view (everything fits and reaches).

Failing that, AFAIK most or all PATA/IDE adapters are supported in Linux. I've got an old Maxtor-branded PATA-100 adapter with a Promise chipset that works fine, but I'm sure it's long out of production. You could check on NewEgg or some other site with customer reviews and look for something with a customer review that mentions Linux, or just buy something from a store with a good return policy in case it doesn't work. There are also numerous Linux hardware compatibility lists on the Web, such as [this Ubuntu-specific one.](http://www.ubuntuhcl.org) Note that, with few exceptions, Linux hardware compatibility is the same from one distribution to another, since hardware device support is determined by the kernel, which is the same in all distributions. (Differences can exist because of different kernel versions or kernel options that are enabled in one distribution but disabled in another.)

---

### Post by teejcee on 2010-04-21
> **srs5694 said:**
> PATA (aka IDE) supports two devices per chain, so you should be able to connect your PATA hard disk to ........... distribution but disabled in another.)

Thank you for your input,srs9694, very much appreciated. 

I've considered the idea of a hdd sharing the interface with the dvd/cd however my understanding is that the speed of PATA is that of the slowest device on the cable, which in this case would be the dvd/cd drive and therefore slowing the hdd somewhat.

Your idea re hardware compatibility is great ( plus the link to the Ubuntu list)... it didn't occur to me to look there.

Thanks again....cheers.

---

### Post by MartyBuntu on 2010-04-21
I've used an Adaptec PCI - IDE card since 6.10.

Never had any problems.

---

### Post by srs5694 on 2010-04-21
The speed issue relates to the *interface speed.* Thus if you've got, say, an IDE-133 DVD drive and an IDE-133 hard disk, the hard disk's speed won't be slowed at all (unless you've got concurrent accesses to both devices, and then the difference would probably be slim to none). You'll need to check the specifications on both the hard disk and the DVD drive to know whether there'll be much of an effect.

---

### Post by teejcee on 2010-04-26
> **MartyBuntu said:**
> I've used an Adaptec PCI - IDE card since 6.10.

Never had any problems.

Thank you...I'll see if I can track one down.

---

### Post by teejcee on 2010-04-26
> **srs5694 said:**
> The speed issue relates to the *interface speed.* Thus if you've got, say, an IDE-133 DVD drive and an IDE-133 hard disk, the hard disk's speed won't be slowed at all (unless you've got concurrent accesses to both devices, and then the difference would probably be slim to none). You'll need to check the specifications on both the hard disk and the DVD drive to know whether there'll be much of an effect.

Thank you....I'll check them out.

---

### Post by teejcee on 2010-05-10
To everyone that helped & to anyone interested, I have solved this issue.

I had a PCI-IDE + SATA & eSATA card in another pc. When I pulled it out I found it was using a VT6421a chipset ( I've had no luck with VT6410 ) so I installed it & presto - works just fine.

Re-installed back to other box, bought a new one & we're away.

Cheers...

---


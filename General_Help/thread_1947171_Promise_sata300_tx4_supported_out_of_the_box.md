---
title: "Promise sata300 tx4 supported out of the box?"
date: 2012-03-26
forum: General Help
---

### Post by r3v0 on 2012-03-26
Hello,

I'm sort of a Linux Newbie.

I succesfully installed a Ubuntu distro (10.04) last year,
and I'm using it most of the time as a server. 
Now I got myself a new case for this PC and tranferred all stuff.
And I had Promise sata300 tx4 controller card laying around and installed that also. I connected a HDD to it. And restarted the PC.
The Promise card recognizes the HDD and than continues to boot. When it's fully booted, it didn't recognize all of the HDDs and the ones which were recognized weren't in the right order. So I thought it might help to upgrade to 11.10. Well after some other trouble I got to 11.10 running normally, but the problems remained. I Tried to compile drivers until i cam across a forum where someone said that these cards are supported out of the box.

So my question is: Is that true?

---

### Post by r3v0 on 2012-03-27
Anyone?

---

### Post by dcstar on 2012-03-27
> **r3v0 said:**
> 
..........
And I had Promise sata300 tx4 controller card laying around and installed that also. I connected a HDD to it. And restarted the PC.
The Promise card recognizes the HDD and than continues to boot. When it's fully booted, it didn't recognize all of the HDDs and the ones which were recognized weren't in the right order.
..........

So how do you know that all the ports on the card actually work?

---

### Post by r3v0 on 2012-03-27
> **dcstar said:**
> So how do you know that all the ports on the card actually work?

Because I took it out of my windows PC a couple months ago where it was fully working.
But do you know if it should work out of the box?

---

### Post by r3v0 on 2012-03-30
After days searching on the internet I found the answer, well sort of.
**Yes! The promise Sata300 TX4 card is supported out of the box.**

The problem I stated in the OP that I missed a HDD and the order was wrong.
Well that was kind of true. The Promise card somehow put himself (the connected HDD) in the first spot thus /dev/sda,
and I guess when I connect more HDDs the places sdb sdc and sdd would be filled before the motherboard HDDs also.
This resulted in mounting the wrong HDDs on my mount points.
I fixed this by editting the fstab file (/etc/fstab) and using UUIDs. 
A detailed howto can be found [HERE]("http://www.cyberciti.biz/faq/linux-finding-using-uuids-to-update-fstab/")

---


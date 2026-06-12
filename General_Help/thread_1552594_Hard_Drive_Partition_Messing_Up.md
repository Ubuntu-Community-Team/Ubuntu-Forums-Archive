---
title: "Hard Drive Partition Messing Up"
date: 2010-08-13
forum: General Help
---

### Post by xiveira on 2010-08-13
Okay to put it short I have reinstalled Kubuntu 10.04 about eight or nine times, I am fed up, so any help in getting this figured out is appreciated. I searched around for a bit and didn't find anything on it; granted I didn't look very hard.

My installs run fine for a while and then the hard drive splits and it screws everything up. I get freezes, program crashes, BusyBox, the works. The installer partitioner thing tells me that my hard drive (sda) then becomes /dev/sda1 and /dev/sda5 (which is around 6.2 gigs, I have a 250 gig hard drive), and I'm pretty sure that sda5 is not supposed to be there because it isn't mine, I did not do it, I dunno what is.

Last time I even ran Kill Disk on it twice and wrote zeros to it. Yet it still keeps happening.

I dunno what else to do. I've tried everything in my arsenal, which is limited at best. Again, any help would be appreciated.

---

### Post by earthpigg on 2010-08-13
what does the disk utility report?

next time you reinstall, i'd try running that in destructive read/write mode from the live cd before doing so.

i have no idea where this utility is on kubuntu, but on ubuntu it's system -> administration -> disk utility. if you cant find it's icon, running 'palimpsest' from the terminal will open it if it's installed on kubuntu by default.

---

### Post by xiveira on 2010-08-13
[http://i35.tinypic.com/ws5rg7.png](http://i35.tinypic.com/ws5rg7.png)

That. lol I wasn't sure what exactly we're looking for so I screencapped for ya. Hehe. And Kubuntu does not have a disk utility thingie by default I had to install it but s'all good~ just in case anyone on Kubuntu is ever lookin fer it. xD

---

### Post by earthpigg on 2010-08-13
yup, that. could have checked the SMART status from the command line, but pointing and clicking is easier. run that from LiveCD and 'check fileystem'. (or do it the command line way, if you wish).

also: have you ruled out that the .iso you downloaded, or CD you burned may be corrupt?

no sense in trying to install the exact same thing from the exact same cd over and over again and expecting different results, ya know?

i suggest checking the md5sum of the .iso and burning again at slowest speed.

---

### Post by Quackers on 2010-08-13
That's your swap partition. Ubuntu needs a swap partition to use when all your ram is in use. It is created by the system if you don't create it yourself.

---

### Post by xiveira on 2010-08-13
O.o if its something the system needs then why is it still kicking like a spooked horse? lol

I ran both of those and both said the drive itself is fine.

Also, the CD should be fine, I ordered it from Canonical. >.>; Nifty design on it, lol

---

### Post by earthpigg on 2010-08-13
oh, wow. i need to pay more attention. 

yeah, it's a swap partition. it's supposed to be there. when you told ubuntu to 'use entire hard drive', that's what it does... including allocating part of it as swap.

---

### Post by xiveira on 2010-08-13
Mk, then... how do I figure out what exactly *is* going wrong with it and why it keeps dropping me into BusyBox? LiveCD is telling me everything is perfectly fine, so it should run fine right?

---

### Post by xiveira on 2010-08-18
Okay. That's really weird.

Never mind, 9.10 decided to be nice and suddenly start working and install flawlessly this morning and it has been running just fine ever since, after two weeks of freaking out on me? Yeah.

Whatev.
Thanks guys.

---

### Post by earthpigg on 2010-08-18
> **xiveira said:**
> Okay. That's really weird.

Never mind, 9.10 decided to be nice and suddenly start working and install flawlessly this morning and it has been running just fine ever since, after two weeks of freaking out on me? Yeah.

Whatev.
Thanks guys.

If you'd told her she was pretty more often, she wouldn't be so erratic.

It's ok though, I'm a pig too.

---


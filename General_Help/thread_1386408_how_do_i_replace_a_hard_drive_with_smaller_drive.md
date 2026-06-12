---
title: "how do i replace a hard drive with smaller drive"
date: 2010-01-20
forum: General Help
---

### Post by Tycho7286 on 2010-01-20
Hi
I have ubuntu server acting as a router installed on a 60 gig drive, i'd like to use that drive in another machine and replace it with a 5 gig drive. how can i transfer from the 60 gig drive to the 5 gig drive?
thanks
 - kev

---

### Post by zollie on 2010-01-20
are you able to connect both drives at the same time?

---

### Post by phillw on 2010-01-20
> **Tycho7286 said:**
> Hi
I have ubuntu server acting as a router installed on a 60 gig drive, i'd like to use that drive in another machine and replace it with a 5 gig drive. how can i transfer from the 60 gig drive to the 5 gig drive?
thanks
 - kev

Hi,

5GB is pretty small. If you do a ```
df -H
```  what do you get on your current set up ?

Phill.

---

### Post by Tycho7286 on 2010-01-20
yes

---

### Post by synapsys on 2010-01-20
The easiest way would probably be to plug in both hard drives, fire up a ubuntu live cd and use gparted to copy/paste partitions. No guarantees because I've never tried it.

PS you may have to shrink the partition to size first.

Backup!!

---

### Post by Tycho7286 on 2010-01-20
> **phillw said:**
> Hi,

5GB is pretty small. If you do a ```
df -H
```  what do you get on your current set up ?

Phill.

826 Megs used

---

### Post by zollie on 2010-01-20
install the OS onto the new drive and then migrate the config files.

that's it.

if you're using it as a router and nothing else, it can't be more than a few iptables lines.

---

### Post by Tycho7286 on 2010-01-20
> **zollie said:**
> install the OS onto the new drive and then migrate the config files.

that's it.

if you're using it as a router and nothing else, it can't be more than a few iptables lines.

I'm not the one who set the router up, so i don't know how it's set up

---

### Post by synapsys on 2010-01-20
> **Tycho7286 said:**
> I'm not the one who set the router up, so i don't know how it's set up

Then you should probably leave it alone.

---

### Post by zollie on 2010-01-20
> **Tycho7286 said:**
> I'm not the one who set the router up, so i don't know how it's set up

i've to tell you, if you plan on messing with a machine and you would not be able to recover in case something went wrong, it's best to leave it alone then.

Setting up an ubuntu router is a piece of cake but there maybe other features you're currently using that you don't know about.

It's always a good practice not to mess with things you can't fix if things were to go south.

---

### Post by Tycho7286 on 2010-01-20
i could set up a new one if i had to, but i'd really rather just clone the drive i have, i also have a dd image file incase anything gets screwed up.

---

### Post by phillw on 2010-01-20
Clonezilla, or the ilk, should be able to handle it for you --> [http://clonezilla.org/](http://clonezilla.org/)   A lot like Norton Ghost - but free :-)

Regards,

Phill.

---

### Post by Tycho7286 on 2010-01-20
> **phillw said:**
> Clonezilla, or the ilk, should be able to handle it for you --> [http://clonezilla.org/](http://clonezilla.org/)   A lot like Norton Ghost - but free :-)

Regards,

Phill.

thanks, but that has the same problem as dd, the destination must be equal or larger than the source.
- kev

---


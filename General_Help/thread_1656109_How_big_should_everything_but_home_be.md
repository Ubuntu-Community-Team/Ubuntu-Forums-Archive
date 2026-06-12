---
title: "How big should everything but home be?"
date: 2010-12-30
forum: General Help
---

### Post by JP121 on 2010-12-30
Hi.

I am trying to move my home directory to its own partition.  I have found the guide that shows how to do this, so I am fine with that.  What I really need to know is how much space I need to leave the partition with everything but home.  Any advice?

Thanks.

---

### Post by Simian Man on 2010-12-30
How big is your hardrive?  How many packages are you planning on installing?

---

### Post by nothingspecial on 2010-12-30
For example.........


Standard install on a laptop with** A LOT** of apps

```
/dev/sda1             6.5G  5.3G  839M  87% /
```

Minimal install with X, openbox and slim (everything else cli)

```
/dev/sda1              12G  2.8G  8.3G  26% /
```

Standard install with (what I would consider) a normal amount of extras
```

/dev/sda4             6.9G  4.2G  2.4G  65% /
```

Now you ask, how come the minimal install has a 12G / and the bloat one has a 6.5G / ?

And I say, because that`s how it is :p

---

### Post by squenson on 2010-12-30
I would give 10% of the total size of your disk to the system partition, with a minimum of 5 GB and a maximum of 30 GB. These are empirical figures based on my experience and I never had any problem of space on the many computers or virtual machines I configured with Ubuntu.

For the smallest systems, you can even consider only one partition, for the system, your data and the swap partition as a file (same performances as if it would be a separate partition).

---

### Post by JP121 on 2010-12-30
> **Simian Man said:**
> How big is your hardrive?  How many packages are you planning on installing?

I have a 160 gb hardrive.  

I don't think I have an insane amount of apps.  Just a base install of Kubuntu, Chrome, Java and an IDE, and maybe something I can't think of.

---

### Post by JP121 on 2010-12-31
I took Dolphin an added all the non home folders in root up.  I had about 5 gigs of data, not counting root and lost and found.  I think I am going to go ahead and give everything to home except for 10 gigs.  That should give me plenty of growing room and plenty of space for home.  I only have 1 gig in home right now anyway, so I think 150 gigs will be plenty of growing room.

---

### Post by deserthowler on 2010-12-31
> **JP121 said:**
> I have a 160 gb hardrive.  

I don't think I have an insane amount of apps.  Just a base install of Kubuntu, Chrome, Java and an IDE, and maybe something I can't think of.

I have a bunch of apps on my 160 GB hard drive and only use about 6 GB for the OS.  However, if you plan to rip a few DVDs to iso with something like k9copy your temp file could become quite large.  If you go about 25-30 GB you should have plenty of room for everything.  This will also allow for doing system upgrades until the machine fails.  This will also leave room to install something like VBOX with a few virtual machines.

Earl

---


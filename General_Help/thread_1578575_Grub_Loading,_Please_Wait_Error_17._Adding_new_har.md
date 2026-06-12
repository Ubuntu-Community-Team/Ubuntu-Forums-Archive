---
title: "Grub Loading, Please Wait Error 17. Adding new hard drive."
date: 2010-09-20
forum: General Help
---

### Post by Snoreis on 2010-09-20
Hello world.

I'm getting a funny error after trying to add a new internal hard drive to my computer.  After adding the new drive to the "Slave" slot GRUB will not load properly and gives me the following error

Grub Loading, Please Wait Error 17

I've checked in my BIOS and the "Master" drive is still the one where grub is loaded.  When I unplug the _new_ drive the problem disappears and I can load Grub normally.  I've searched the threads, but couldn't find a similar problem, or a problem that could be applied to mine.

I've also tried loading the live CD, but my internal CD drive is broken, and the external one I have doesn't seem to recognized during boot time.

Any suggestions or links that can help either of these problem?

Thanks

---

### Post by coffeecat on 2010-09-20
I've had to make a few assumptions here based on what you've said, so here goes.

By using the terms 'slave' and 'master' for your HDDs, I guess your machine takes the older standard PATA IDE drives, where you connect both drives to the motherboard with one wide ribbon cable. Correct?

And grub error 17 suggests legacy grub which means either that you are running 9.04 or earlier, or that your 9.10 or 10.04 is a dist-upgrade from a pre-9.10 version. Correct?

Anyway. From the legacy grub manual:

> 17 : Cannot mount selected partition

This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB.Don't read too much into that. Error 17 seems to come up a lot when grub can't make out what's going on, so that may not mean an unrecognisable filesystem at all.

I have one suggestion for now, and if that doesn't work then we can take it from there. Have a look at the jumpers on the two drives. Are both or either set to cable-select? If so, change them so that the master is set to master and slave to slave. The actual jumper position varies from make to make but should be printed on the drive label. Cable-select is utterly unreliable and I have had some decidedly odd things happen when using it.

---

### Post by Snoreis on 2010-09-20
Thanks for the reply.

To answer some of your questions:

Yes, the machine is an older IDE computer with the wide ribbon cable.

I'm not sure what you mean by Cable-Select, however, the flat ribbon cables are labeled with "Master" and "Slave" at the respective connectors.

One other thing I'd like to note is that the new drive is a SATA drive with a SATA to IDE adapter attached.  Everything is plugged in solid as far as I am concerned as the computer boots up normally if the "new" drive is not connected correctly.

---

### Post by Snoreis on 2010-09-20
Also, if I hold down the "Esc" key when grub is loading, I get "Error 18" instead of "Error 17"

---

### Post by Snoreis on 2010-09-20
Oh, and yes, I am currently using version 8.04  Is it worth it to upgrade and then try again?

---

### Post by coffeecat on 2010-09-20
> **Snoreis said:**
> I'm not sure what you mean by Cable-Select, however, the flat ribbon cables are labeled with "Master" and "Slave" at the respective connectors.

OK, the ribbon cable is not the problem. Have a look at the actual drive, at the connector end, between the data ribbon cable connector and the molex (4-pin) power connector. You'll see a small area with about 8-9 thin pins, the same size as the data pins. There will be 1 or 2 plastic jumpers shorting out a couple of the pins. Either on the label on the flat surface of the drive, or on a label above the connectors you will see small diagrams showing you the positions of the jumpers for master, slave and cable-select. The idea of cable-select was meant to be a time saver. You didn't bother with changing the jumper position if you moved the drive around, because (in theory) the master or slave status was determined by which bit of the ribbon cable it was attached to. In practice it often falls down. So - with your master drive, make sure the jumper is in the master position, not the cable-select.

However....

> **Snoreis said:**
> One other thing I'd like to note is that the new drive is a SATA drive with a SATA to IDE adapter attached.

This may be the problem. I've no experience of such things, but check to see if there is a jumper on the ide side of the adapter, and set it to slave if there is. Jumper selection is fundamental when using ide drives but if that adapter relies on cable-select that could be problematic.

---

### Post by coffeecat on 2010-09-20
> **Snoreis said:**
> Oh, and yes, I am currently using version 8.04  Is it worth it to upgrade and then try again?

I'm not sure that would help. If you upgrade to 10.04, you'll still have the same legacy grub. If you did a fresh install of 10.04 you'd get grub 2, but I doubt that would cope any better. This cable-select business may not be the problem, but we need to get it out of the way.

**Edit:**

> **Snoreis said:**
> Also, if I hold down the "Esc" key when grub is loading, I get "Error 18" instead of "Error 17"

I missed that post when I was posting. That's an interesting one:

> 18 : Selected cylinder exceeds maximum supported by BIOS
This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB in general).What sizes are the two drives? Disregard the 8GB, but it might be that your BIOS cannot handle the size of the SATA drive.

---

### Post by Snoreis on 2010-09-20
> **coffeecat said:**
> You'll see a small area with about 8-9 thin pins, the same size as the data pins. There will be 1 or 2 plastic jumpers shorting out a couple of the pins. Either on the label on the flat surface of the drive, or on a label above the connectors you will see small diagrams showing you the positions of the jumpers for master, slave and cable-select. 


Ok, so I found the jumpers and rearranged them to the "Master" position.  Still getting the same behavior however.  When the new drive is plugged in I get the Error 17, and when it is disconnected Ubuntu loads normally.  I could not find any jumpers or a way to select "Master" or "Slave" on the adapter.

---

### Post by Snoreis on 2010-09-20
> **coffeecat said:**
> 
What sizes are the two drives? Disregard the 8GB, but it might be that your BIOS cannot handle the size of the SATA drive.

Yea that may be it, the new one I'm adding is 500gigs.  The original drive is only 120.

---

### Post by coffeecat on 2010-09-21
> **Snoreis said:**
> Ok, so I found the jumpers and rearranged them to the "Master" position.  Still getting the same behavior however.  When the new drive is plugged in I get the Error 17, and when it is disconnected Ubuntu loads normally.  I could not find any jumpers or a way to select "Master" or "Slave" on the adapter.

> **Snoreis said:**
> Yea that may be it, the new one I'm adding is 500gigs.  The original drive is only 120.

Sorry for the delay in getting back. It was late last night and I had to log off.

Anyway, a few thoughts:

My first self-build machine for Linux, a little over 5 years ago, had the normal for the time 2 motherboard IDE connectors for hard drives and optical drives, but also had one SATA header on the motherboard. It may have been a little ahead of its time because it was a +1 year-old design when i bought it in 2005. I'm sure you would have bought the ide/sata adapter because there is no sata header, but it might be worth double-checking. Do you have the motherboard manual? Do you know the make and model number? If that was an OEM prebuilt machine, the motherboard model number might be printed on it. If there is a SATA header, this would bypass the ide/sata adapter which might be the problem

Have a look on the SATA drive. There should be a jumper as with the IDE drive, but for a different purpose, changing the default 3.0 Gbps transfer speed to 1.5 Gbps. This would slow the drive down, but it may be that your motherboard cannot support the faster 3.0 Gbps. Good luck though. I'm looking at a Samsung drive which has a clear diagram for the jumper settings and a Maxtor which has a jumper but no diagram. (I never did like Maxtor as a brand.)

With larger IDE drives, the jumper could also be used to limit its effective size to 32GB to cope with older BIOS's that can't read larger drives. I doubt whether you can do that with SATAs but it might be worth checking when you look at the jumper.

I'm not convinced, though, that the drive size is the issue. The grub error is inconsistent. I just hope that your motherboard is recent enough to have a SATA header - that would be the best option although you may have to enable it in the BIOS if one is there.

---

### Post by belikralj on 2010-09-21
Hmmm, I've had this happen to me twice but I don't remember how I solved it. However the selection of the correct master/slave seems a logical first step and there is one thing you might not have tried...

Was your original drive (the non-sata one) the master or the slave? This matters because linux labels the drives according to their position in the actual computer. Forgive me if you already know this but I'll just explain it a little just in case.

**Explanation follows**: (skip this bit if you don't care about the "why?")

If you plug in your hard disk with the IDE cable slot 1 on the mother board that cable can have two hard disks attached. One will be the master and the other the slave. The master will be labeled as ```
/dev/hda
``` and the slave will be labeled ```
/dev/hdb
``` similarly if you plug a cable into the IDE number 2 slot in the motherboard the master will be labeled ```
/dev/hdc
``` and the slave ```
/dev/hdd
```

Now I've said this because if grub thinks your disk is in ```
/dev/hda3
``` (it refers to the third partition on the master drive connected to IDE slot 1) and you take that drive out and put it elsewhere and plug another drive into that same connection it might get a little confused as to which drive is which... 

This is the assumption that we have made, BUT... With Ubuntu 8.04 UUID's have been used instead of designated drives because they make it easier to identify the drive if you are using even if you switch them so I'm not sure if this will actually fix it. Similarly it might be named ```
/dev/sda
``` instead of ```
/dev/hda
``` but the naming idea is the same.

**Explanation ends**.

So long story short, try switching which drive is the master and which is the slave... I'm not sure of what the setup inside your computer is exactly so it might not work but this is the best I can come up with atm.

---


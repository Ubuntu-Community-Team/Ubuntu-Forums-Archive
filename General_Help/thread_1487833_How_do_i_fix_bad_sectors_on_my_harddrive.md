---
title: "How do i fix bad sectors on my harddrive"
date: 2010-05-19
forum: General Help
---

### Post by thingy87654321 on 2010-05-19
I Have a seagate Serial ATA 250GB harddrive in my computer that is partitioned into multiple partitions, i have 4 bad sectors that the disk utilty says is fixable, how do i fix them? i know this is a noob-ish question

:popcorn: Waits for answer :popcorn:

p.s. im running 10.04 Lucid Lynx


(im also a noob at taking screen shots, as you can see)

---

### Post by 3Miro on 2010-05-19
From what I know you cannot fix a bad sector, this is a hardware not a software issue. What the system can do is stop using those sectors and hopefully this will not result in lost data. This should be done automatically.

Keep an eye on the number of bad sectors, once hard disks start going bad, they go bad fast. If you see the number going up, you should get a new hard drive.

---

### Post by philinux on 2010-05-19
Like it says the self assessment says Passed.

The disks own S.M.A.R.T system will already have remapped them. Just make sure you backup regularly and keep an eye on the count.

If you search re smart you should get some idea of how it works.

You'll get a warning if the disk is failing anyway.

---

### Post by thingy87654321 on 2010-05-21
I read from some site a while back that it is possible to remap thoose bad sectors, is this just B.S. or is it possible?

---

### Post by bodhi.zazen on 2010-05-21
> **thingy87654321 said:**
> I read from some site a while back that it is possible to remap thoose bad sectors, is this just B.S. or is it possible?

To make a technical discussion short - This is handled by the hardware automatically (aka "firmware" or the Hard disk drivers).

It is wear an tear on the hard drive and once it gets to the point where it starts to affect your data it is time to get a new hard drive.

Keep in mind, all disks have some bad sectors, so as with all data important, back up 

See also :

[http://www.linuxjournal.com/magazine/monitoring-hard-disks-smart](http://www.linuxjournal.com/magazine/monitoring-hard-disks-smart)

[http://www.fix-hdd-bad-sectors.com/](http://www.fix-hdd-bad-sectors.com/)

---

### Post by thingy87654321 on 2010-05-21
which means i have one harddrive with a lot of bad sectors i was hoping to put in my xbox 360, and this one which isnt very old, it was from a external HDD from seagate, since this one is dieing and i have all my files on it, i guess its time to buy a new one... :(. i need money

---

### Post by linuxman94 on 2010-05-21
> **thingy87654321 said:**
> which means i have one harddrive with a lot of bad sectors i was hoping to put in my xbox 360, and this one which isnt very old, it was from a external HDD from seagate, since this one is dieing and i have all my files on it, i guess its time to buy a new one... :(. i need money

You do not need to buy a new hardrive yet, it only has a few bad sectors.  But is that number increases and it fails the S.M.A.R.T test, then you need a new one.

---

### Post by elliotn on 2010-05-21
u cant fix it, its dying

---

### Post by bodhi.zazen on 2010-05-21
Back up your data , reformat the disk, restore your data.

The formatting process is how this is "fixed". It is not a fix in that your HD is still failing, it is a fix in that your file system marks the bad sectors as bad during the formating process.

Eventually all HD fail, use this one as long as possible.

If the data is important to you, you need an external back up, off the hard drive (CD / DVD / flash drive), no matter how new or old the drive may be.

---

### Post by bcfieldi on 2010-10-30
There is a program called spinrite. Unfortunately you have to pay for a 'legal' version of this software but it is well worth it. And I don't say that about any type of software. Spinrite will reallocate bad sectors that it cannot fix, but for the most part, it will be able to fix them. The program actually physically turns every 1 to a 0 and 0 to a 1 and then back again, resurfacing and resurrecting your HD. I was looking for an alternative to the program (if there was one) and came across this older post but I figured someone else might gain from it even if it's already too late for you.

---


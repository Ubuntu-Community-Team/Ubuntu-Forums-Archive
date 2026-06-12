---
title: "Unable to mount partition on boot"
date: 2010-03-28
forum: General Help
---

### Post by Aquatic Fist on 2010-03-28
I have a problem with my laptop. I have Ubuntu 10.04 Lucid Lynx installed.

Everytime I start the laptop it works fine til the GNU GRUB page. There I choose:

> Ubuntu, Linux 2.6.32-17-genericThen it says:

> fsck from util-linux-ng 2.17.2
Ubuntu_[32_GB] was not cleanly unmounted, check forced
udevd[328]: can not read '/etc/udev/rules.d/z80_user .rules'Then it checks for errors and says:

> Your disk drives need to be checked for errors, this may take some time
Checking disk 1 of 1 (XX% complete)

Press C to skip the disc checkWhen it reaches 100% it says:

> Failed to mount /media/Windows [SM]If I press C it says the same thing:

> Failed to mount /media/Windows [SM]So what should I do? Is it something I can do myself or do I have to leave it in or something?

---

### Post by Ben Crisford on 2010-03-28
Hmm, did you force shutdown last time you booted successfully?  (by that I mean hold down the "on" button rather than go through the motions of shutting down the long way)

If you did then that could explain Ubuntu not unmounting properly...

---

### Post by Aquatic Fist on 2010-03-28
Well, not before the first time this happened, but when it said "Failed to mount /media/Windows [SM]" I couldn't do anything else than force it to shutdown.

---

### Post by Ben Crisford on 2010-03-28
Hmm, I can't think of why it might be that you are experiencing these problems...

If you boot a live cd, can you mount your ubuntu partition?

---

### Post by Aquatic Fist on 2010-03-28
I booted the live CD and chose "Try Ubuntu without..." And then the partitions were mounted. So I restarted the Laptop (not force shutdown) but it still didn't work. It said something more about the clock but otherwise, no difference. Maybe I shall reinstall Ubuntu. Also the live CD wasn't 10.04. It was an older version of Ubuntu like 9.04 or something.

---

### Post by Aquatic Fist on 2010-03-29
Oops, double post...

Well, this is what I decided to do.

I have now made a backup of all the things I want to keep like was located in the Ubuntu Partition. I have now placed documents, fonts, etc in my old Windows 7 partition. So now I'm going to make a new Ubuntu install on the Ubuntu partition using this live CD. 

Also, thanks Ben Crisford for reminding me about the live CD. I had actually forgot I used it to install Ubuntu. I thought I used a Flash Drive or something :P

---


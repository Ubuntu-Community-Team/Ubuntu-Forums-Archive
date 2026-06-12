---
title: "what the hell is going on with my hard drive"
date: 2009-07-17
forum: General Help
---

### Post by thirdeye420 on 2009-07-17
Hi everyone,

for those who haven't seen my earlier posts, i'll summarize.  My old hard drive crashed, I got a new one to replace it, but it wasn't being detected in my bios or when i was trying to install ubuntu.  I fired it up last night, checked my bios and it detected it, so i got ubuntu installed.  I started downloading and installing updates, and the computer froze up.  I restarted the computer and got a boot error.  checked the bios, says there is no hard drive?  I don't understand lol...

---

### Post by uberlube on 2009-07-17
depending on how old your motherboard is i suggest getting yourself a new cmos battery possibly. That would save you from having to set up the boot order every time u log in. If thats not the issue it could be your board about to bite the dust. Get yourself a copy of partedmagic and boot it live. Try to see if you can mount the HD in there and set up your partitions there, might help fix the issue.

---

### Post by az on 2009-07-17
> **thirdeye420 said:**
> Hi everyone,

for those who haven't seen my earlier posts, i'll summarize.  My old hard drive crashed, I got a new one to replace it, but it wasn't being detected in my bios or when i was trying to install ubuntu.  I fired it up last night, checked my bios and it detected it, so i got ubuntu installed.  I started downloading and installing updates, and the computer froze up.  I restarted the computer and got a boot error.  checked the bios, says there is no hard drive?  I don't understand lol...

It sounds like a hardware problem.  It may be your motherboard, your connections, your power supply....

---

### Post by HavocXphere on 2009-07-17
> **thirdeye420 said:**
> says there is no hard drive?  I don't understand lol...
That is not good. :redface:

First, check the physical connections of the drive. Sometimes thermal expansion can make things a bit flakey.

If that doesn't help, then check if the drive spins-up when you start the PC. If it does not then its dead. In that case you can start googling for "harddrive freezer trick". Fairly risky, but might make the drive work again for a short time only.

If it is however spinning up then try putting it in another PC. Or another channel (IDE/SATA). Also try another power cable (PSU-Harddrive).

The BIOS _must_ recognize it. If it doesn't then nothing can talk to the drive.(Not even Ubuntu or Chuck Norris).

---

### Post by thirdeye420 on 2009-07-17
i have played with all the connections.  this drive has always worked before.  i dont understand why it would detect it, then all of a sudden, won't detect it.  my motherboard is an ASUS approx 6 years old now (my cpu is an AMD barton 2600 XP 1.8 GHz).  Do you think maybe it's becoming toast?

---

### Post by Grenage on 2009-07-17
I'd put money on your motherboard being the cause of the problem; on the plus side that means your old drive may be fine.  Motherboards generally go due to a defective PSU, and rarely due to 'just failing'.

---

### Post by thirdeye420 on 2009-07-17
psu?

---

### Post by Grenage on 2009-07-17
Power Supply Unit (or just Power SUpply).  Regardless of whether it was or was not the cause, the motherboard will already be damaged.

This is of course mere conjecture, as I don't have the machine in front of me.

---

### Post by Shazaam on 2009-07-17
psu= power supply.
I agree, change the motherboard battery. Make sure you UNPLUG the pc first. :)

---

### Post by thirdeye420 on 2009-07-17
can you get a battery at any PC store?  if this doesn't work, then i'm guessing I should maybe invest in a new computer.

---

### Post by Grenage on 2009-07-17
I'm sorry, but I have to speak up here; buying a battery will be a waste of your time and money.  There isn't a chance in hell it will help.

---

### Post by LightningCrash on 2009-07-17
> **thirdeye420 said:**
> can you get a battery at any PC store?  if this doesn't work, then i'm guessing I should maybe invest in a new computer.

You can get them at Walmart for a few bucks. Go over to the Camera section and pick up a CR2032 battery. Buy a spare if you can :D

I'd still put money on it being the motherboard/cpu/PSU though

---

### Post by Shazaam on 2009-07-17
Yes. Either write down the number on the battery or take it with you to the store. Once you replace the battery you will have to adjust your bios to your liking. There might be a "default" setting that you can choose then "Save and Exit". If you haven't manually adjusted the bios before that is probably the choice you want.
There are different keys/key combos used to access the bios screen; holding down the "Delete" key as the pc boots is one of the ways to do it.

---

### Post by thirdeye420 on 2009-07-17
how come this is only affecting my hard drive and not my cdroms or disk drive?

---

### Post by Grenage on 2009-07-17
Are they on the same controller?

---

### Post by thirdeye420 on 2009-07-17
no,  hard drive and floppy drive are on the same controller, floppy drive is still being detected

---

### Post by HavocXphere on 2009-07-17
Battery will not help.

Problem: BIOS not detecting drive.

Battery: Needed to store detected info. If there is no info then there's nothing to store.

---

### Post by Grenage on 2009-07-17
Who knows, they're a different kettle of fish, ultimately responding to polls instantly (no delay or 'spin up).  Try the drive on another computer.

Bottom line, it'll be the motherboard, and possibly the PSU as the cause.

---

### Post by thirdeye420 on 2009-07-17
well its an old computer anyways, good excuse to go out and get something a bit newer.  If i could get this one functional long enough to take it to a 2nd hand computer shop to sell then I would be happy.

---

### Post by thirdeye420 on 2009-07-21
ok, changed the battery...nothing, changed the IDE cables... nothing, changed the power supply...nothing.  I'm still getting DISK BOOT ERROR messages when i boot up.  my motherboard must be screwed...

---


---
title: "Install Kubuntu on a SCSI drive?"
date: 2009-09-25
forum: General Help
---

### Post by jlacroix on 2009-09-25
At work, we are decommissioning a Unix server. They have offered this server to me to keep, however I don't have room for it in my apartment. I did ask to take the hard drives though, and I have four 18GB 15k Ultra320's with me right now and I'll strip the rest of them out later.

Here is what I am thinking. On my desktop computer at home, I want to put my root partition for Kubuntu on one of these drives, and then I will have my /home partition on a completely separate SATA hard drive. Then I am going to clone my root partition on to each SCSI drive, so if one dies I have my OS on another I can swap in. I would probably benefit from even faster OS speed.

However, here's the problem. I've never done this before. I've never actually used SCSI. I obviously need to buy a SCSI card, but which one? I need one that Kubuntu is compatible with, that fits within my budget. What do you guys recommend I buy? If you have one and are using it now, what model is it? I need one compatible with these Ultra320 drives so any advice would rock.

I figured this would be a really fun project to do at home. :)

---

### Post by sedawk on 2009-09-25
It might be fun, expensive and loud ;-)

When adding a SCSI controller and one or more
disk drives your PC will also consume more
power and the disk drives might be very loud.

You already have two drives, so while backup is
a good idea think about using the second drive
(or an external USB drive) as a backup medium.
(Normally you do not have to backup the root
 partition or OS. Reinstalling OS from CD is
 most likely much easier than messing around
 with backup procedure for OS recovery.
 Backup your home directory and any other important
 stuff you changed. Especially if you added 
 non-standard software (self-compiled sources) keep
 track of what you added and changed).

---

### Post by alphaniner on 2009-09-25
I've used innumerable different models of LSI and Adaptec cards with Ubuntu at work and never had a problem.  You will have to configure the card's BIOS to pass the drive to the mobo BIOS (which will have to be configured to boot from the SCSI card), but that's really all there is to it.

---

### Post by jlacroix on 2009-09-25
> **sedawk said:**
> It might be fun, expensive and loud ;-)

When adding a SCSI controller and one or more
disk drives your PC will also consume more
power and the disk drives might be very loud.

You already have two drives, so while backup is
a good idea think about using the second drive
(or an external USB drive) as a backup medium.
(Normally you do not have to backup the root
 partition or OS. Reinstalling OS from CD is
 most likely much easier than messing around
 with backup procedure for OS recovery.
 Backup your home directory and any other important
 stuff you changed. Especially if you added 
 non-standard software (self-compiled sources) keep
 track of what you added and changed).

Actually, I have since removed the 160GB drive from my machine (I forgot to update the signature). The 320GB drive will also be removed in favor of a 1.5TB drive.

As far as using them to back up personal data, that's not going to work. My 320GB drive is almost completely full with personal data. (I'm not kidding). Not only that, but I use Unison to sync my home directory to my laptop AND an external hard drive, so backups aren't an issue for me. I have DVD's of a lot of my stuff too.

Are SCSI drives really that much louder than a SATA drive?

> **alphaniner said:**
> I've used innumerable different models of LSI and Adaptec cards with Ubuntu at work and never had a problem.  You will have to configure the card's BIOS to pass the drive to the mobo BIOS (which will have to be configured to boot from the SCSI card), but that's really all there is to it.

I should be able to boot off of the SCSI drive, right?

---

### Post by alphaniner on 2009-09-25
> **jlacroix said:**
> Are SCSI drives really that much louder than a SATA drive?

It has nothing to do with SCSI, I suspect he said that because of the RPM of the drive.

> **jlacroix said:**
> I should be able to boot off of the SCSI drive, right?

Absolutely, it will just take some BIOS configuration to make it work.

Also, how well do you understand SCSI cabling (IDs and termination)?

---

### Post by jlacroix on 2009-09-25
How much do you guys think it will be to get a SCSI card?

---

### Post by alphaniner on 2009-09-25
> **jlacroix said:**
> How much do you guys think it will be to get a SCSI card?

For a 320 card, around a couple hundred bucks new.

[http://www.google.com/products?q=LSI20320IE&aq=f]("http://www.google.com/products?q=LSI20320IE&aq=f")

Here's a link to LSIs current [SCSI HBAs]("http://www.lsi.com/storage_home/products_home/host_bus_adapters/scsi_hbas/index.html").  Also, mind the interface.  You can't get 320 speeds on a standard PCI slot.  All 320 cards are going to be PCI-X (PCI Extended, mostly found in server boards) or PCI-E (PCI Express, what your Graphics card probably uses).

---

### Post by jlacroix on 2009-09-25
> **alphaniner said:**
> For a 320 card, around a couple hundred bucks new.

[http://www.google.com/products?q=LSI20320IE&aq=f]("http://www.google.com/products?q=LSI20320IE&aq=f")

Here's a link to LSIs current [SCSI HBAs]("http://www.lsi.com/storage_home/products_home/host_bus_adapters/scsi_hbas/index.html").  Also, mind the interface.  You can't get 320 speeds on a standard PCI slot.  All 320 cards are going to be PCI-X (PCI Extended, mostly found in server boards) or PCI-E (PCI Express, what your Graphics card probably uses).

My Videocard uses a PCI-Express 16 slot, but I think I have a PCI Express 1x slot available.

---

### Post by alphaniner on 2009-09-25
Both of the LSI 320 cards require a 4x slot.

Edit: Actually, 4x 'or greater' as it could be installed into an 8x or 16x PCI-E slot.

---

### Post by jlacroix on 2009-09-25
> **alphaniner said:**
> Both of the LSI 320 cards require a 4x slot.

Hmmm, that might be a challenge. There's no such thing as a SATA to SCSI converter cable, is there?

Edit: I found this:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16816103045&cm_re=PCI_1x_scsi_card-_-16-103-045-_-Product](http://www.newegg.com/Product/Product.aspx?Item=N82E16816103045&cm_re=PCI_1x_scsi_card-_-16-103-045-_-Product)

---

### Post by alphaniner on 2009-09-25
> **jlacroix said:**
> Edit: I found this:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16816103045&cm_re=PCI_1x_scsi_card-_-16-103-045-_-Product](http://www.newegg.com/Product/Product.aspx?Item=N82E16816103045&cm_re=PCI_1x_scsi_card-_-16-103-045-_-Product)

That should work, although I'd be hesitant based on the user reviews.

And doesn't your mobo have two 16x slots?

---

### Post by jlacroix on 2009-09-25
> **alphaniner said:**
> That should work, although I'd be hesitant based on the user reviews.

And doesn't your mobo have two 16x slots?

That's right! Totally forgot about that!!! I was using the other one for SLI but I've since decomissioned SLI on my machine, since there wasn't much of a benefit.

What is your recommendation on a good (and hopefully affordable) PCI Express 16 SCSI card?

---

### Post by alphaniner on 2009-09-25
I don't know if there are any 16x cards, but I'd recommend the [LSI 20320IE]("http://www.lsi.com/storage_home/products_home/host_bus_adapters/scsi_hbas/lsi20320ie/index.html").  It can be plugged into your 16x slot.

---

### Post by jlacroix on 2009-09-25
> **alphaniner said:**
> I don't know if there are any 16x cards, but I'd recommend the [LSI 20320IE]("http://www.lsi.com/storage_home/products_home/host_bus_adapters/scsi_hbas/lsi20320ie/index.html").  It can be plugged into your 16x slot.

Is that a 4x card? Are you saying a 4x card can be plugged into a 16x slot? If so, that's something I never knew.

---

### Post by alphaniner on 2009-09-25
It's a 4x card.  Any PCI-E card can be plugged into a 'larger' PCI-E slot.  There may be exceptions, but this is the rule.

I use a 4x LSI SAS MegaRAID card in a 16x slot.

---

### Post by jlacroix on 2009-09-25
> **alphaniner said:**
> It's a 4x card.  Any PCI-E card can be plugged into a 'larger' PCI-E slot.  There may be exceptions, but this is the rule.

I use a 4x LSI SAS MegaRAID card in a 16x slot.

Awesome. Do those come with a SCSI cable as well?

---

### Post by alphaniner on 2009-09-25
> **jlacroix said:**
> Awesome. Do those come with a SCSI cable as well?

I doubt it.  SCSI cabling is a discipline in itself.  Ok, that's a bit of an exaggeration.  The length of the cable and the number of connectors will depend on how many of those drives you intend to use.  And you need to make sure your cable and terminator are 320 certified.

Honestly, you'd probably be better off selling the server and drives on ebay and buying some SAS hardware.  Out of curiosity, what kind of server is it?

---

### Post by jlacroix on 2009-09-25
> **alphaniner said:**
> I doubt it.  SCSI cabling is a discipline in itself.  Ok, that's a bit of an exaggeration.  The length of the cable and the number of connectors will depend on how many of those drives you intend to use.  And you need to make sure your cable and terminator are 320 certified.

Honestly, you'd probably be better off selling the server and drives on ebay and buying some SAS hardware.  Out of curiosity, what kind of server is it?

It's an HP-UX server. I'd sell the drives on ebay but I don't want to do that unless I can wipe them. I don't know of any way to wipe them without having them installed on a card.

---

### Post by alphaniner on 2009-09-25
> **jlacroix said:**
> I don't know of any way to wipe them without having them installed on a card.

Yeah, you're in a bit of a pudding there.  Can't help ya with that.  Good luck.

---

### Post by jlacroix on 2009-09-25
> **alphaniner said:**
> Yeah, you're in a bit of a pudding there.  Can't help ya with that.  Good luck.

Thank you guys for everything.

---

### Post by egalvan on 2009-09-25
> **jlacroix said:**
> It's an HP-UX server. I'd sell the drives on ebay but I don't want to do that unless I can wipe them. I don't know of any way to wipe them without having them installed on a card.

If the server is still operational at work, then download 

Darik's Boot And Nuke

dban.org

ti will wipe anything.

---

### Post by egalvan on 2009-09-25
as for where to get inexpensive SCSI cards,

on eBay, and search for

Adaptec <-- a good brand
SCSI
160 <-- these are transfer speeds
320 <--
LVD <-- a type of SCSI connector

depending on what you want/need


BTW,these are good drives, small, but fast and furious.
18GB 15k Ultra320

Not THAT loud, I have two.

And keep in mind, they are used, so life-span may be limited...
don't use them for critical data.


And you CAN  use Ultra320 on Ulra160 or less,
the critical specs are the style of interface
SCA  <-- 80 pin
68P <-- 68 pin
(and there are adpaters for this)

and the type

LVD
Single-ended

matching end-to-end is best, of course.

---

### Post by jlacroix on 2009-09-25
> **egalvan said:**
> If the server is still operational at work, then download 

Darik's Boot And Nuke

dban.org

ti will wipe anything.

The server is no longer operational. It was nice to us, and I'm sad to see it go. (Especially because the morons replaced it with a Windows server!!!!!!!!!)

> **egalvan said:**
> as for where to get inexpensive SCSI cards,

on eBay, and search for

Adaptec <-- a good brand
SCSI
160 <-- these are transfer speeds
320 <--
LVD <-- a type of SCSI connector

depending on what you want/need


BTW,these are good drives, small, but fast and furious.
18GB 15k Ultra320

Not THAT loud, I have two.

And keep in mind, they are used, so life-span may be limited...
don't use them for critical data.


And you CAN  use Ultra320 on Ulra160 or less,
the critical specs are the style of interface
SCA  <-- 80 pin
68P <-- 68 pin
(and there are adpaters for this)

and the type

LVD
Single-ended

matching end-to-end is best, of course.

Thank you. Ebay it is then. :)

---


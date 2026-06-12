---
title: "IDE on SATA connection"
date: 2011-10-24
forum: General Help
---

### Post by Formerly on 2011-10-24
Maybe it's the wrong forum. My computer uses SATA hard drives, but I want to connect an IDE hard drive to it. I know there are converters, but I'm not sure which I will need; there seem to be many types.

My computer has a connection for a second hard drive all ready to go, but it's the 'bigger' connection. I notice a lot of IDE to SATA connections offer the 'small connection. Not only that but it is to say I already have a connector ready to use, it just needs a slot to pop it into.

Anyone know what kind of product I would be looking for, specifically?

---

### Post by dave01945 on 2011-10-24
I'm not sure what you mean by "bigger connection" can you explain abit more

I know you can get SATA to IDE converters on ebay but I hear they don't last very long you could try a more expensive one but that may have the same issues.

The best way in my opinion would be to get a PCI/PCI-e card that has an IDE socket on it

---

### Post by PaulInBHC on 2011-10-24
If it is just for data storage you can get an enclosure to put the HDD in that plugs into a USB socket for around $20.

---

### Post by donkyhotay on 2011-10-24
BTW this is the "gaming and leisure" forum, this really should be posted in general help or absolute beginner talk.

---

### Post by Perfect Storm on 2011-10-25
Thread moved.

---

### Post by kurt18947 on 2011-10-25
> **dave01945 said:**
> I'm not sure what you mean by "bigger connection" can you explain abit more

I know you can get SATA to IDE converters on ebay but I hear they don't last very long you could try a more expensive one but that may have the same issues.

The best way in my opinion would be to get a PCI/PCI-e card that has an IDE socket on it

I'm guessing "bigger connection" refers to the 40 pin IDE connector vs. 4 pin SATA connector. I bought a couple PATA -> SATA converters from Monoprice and they seemed to work okay -- they're SATA1 only but I think that's still faster than IDE so no loss there. Mine do require a "floppy" power connector so you'd need to make sure one is available.
[http://www.monoprice.com/products/subdepartment.asp?c_id=104&cp_id=10407](http://www.monoprice.com/products/subdepartment.asp?c_id=104&cp_id=10407)

---

### Post by Robertjm on 2011-12-06
Are the drives actually recognized as boot drives, or only as data drives after booting into the o/s?

Have you tried any dual partitioned drives with these (W7 and Ubuntu)?

I ordered a Masscool Pci-express card, which has the 40-pin socket on it. However, it's going back. The socket is facing out from the face of the card, and is "upside down" so even a thin IDE cable has to double over itself before going to the IDE drives, which eats up some length AND either blocks another slot or leans up against the next card. I like these dongle options better.

Robert

> **kurt18947 said:**
> I'm guessing "bigger connection" refers to the 40 pin IDE connector vs. 4 pin SATA connector. I bought a couple PATA -> SATA converters from Monoprice and they seemed to work okay -- they're SATA1 only but I think that's still faster than IDE so no loss there. Mine do require a "floppy" power connector so you'd need to make sure one is available.
[http://www.monoprice.com/products/subdepartment.asp?c_id=104&cp_id=10407](http://www.monoprice.com/products/subdepartment.asp?c_id=104&cp_id=10407)

---

### Post by kurt18947 on 2011-12-06
> **Robertjm said:**
> Are the drives actually recognized as boot drives, or only as data drives after booting into the o/s?

Have you tried any dual partitioned drives with these (W7 and Ubuntu)?

I ordered a Masscool Pci-express card, which has the 40-pin socket on it. However, it's going back. The socket is facing out from the face of the card, and is "upside down" so even a thin IDE cable has to double over itself before going to the IDE drives, which eats up some length AND either blocks another slot or leans up against the next card. I like these dongle options better.

Robert

Hi Robert

No, I haven't tried dual boot drives.  The IDE drive is seen as a SATA drive so it may/should work but I have no experience with it. One aspect of the SATA adapter that took a little tinkering was jumpering the IDE hard drive.  It was a Western Digital and I was running it on an IDE cable with no jumpers.  I had to jumper it as master in order for the SATA adapter to see it.  That drive has since gone to hard drive heaven so I'm not currently using an IDE/SATA adapter.

---

### Post by Robertjm on 2011-12-06
Good to know as I'm running a couple WD drives here as well.At least, until SATA drive prices come back down in a few months and I can copy my data over to them.

Robert

> **kurt18947 said:**
> Hi Robert

No, I haven't tried dual boot drives.  The IDE drive is seen as a SATA drive so it may/should work but I have no experience with it. One aspect of the SATA adapter that took a little tinkering was jumpering the IDE hard drive.  It was a Western Digital and I was running it on an IDE cable with no jumpers.  I had to jumper it as master in order for the SATA adapter to see it.  That drive has since gone to hard drive heaven so I'm not currently using an IDE/SATA adapter.

---

### Post by Artemis3 on 2011-12-07
Buy the ones with a 90degree angle, they are meant to be plug directly in your HDs, and then run the sata cable to the mb.

The straight ones are the other way around, to plug in a pata socket on the motherboard, then a sata cable to the sata disk.

These things are not clearly labeled, thats the only hint i know to recognize them, and have purchased the wrong ones already ^^!

Wrong one (Pata to Sata, straight):
[img]http://images.highspeedbackbone.net/skuimages/large/B200-1094-large.jpg[/img]

Correct one (Sata to Pata, 90deg angle):
[img]http://www.amazool.com/images/products_images/unfurl/amazool_b253_shop.jpg[/img]

Yes the adapter needs its own power.

Example usage of the wrong one, note its straight:
[img]http://www.memkingdom.com/Lowyat/SATAtoIDE/SATAtoIDE.jpg[/img]

Example usage of the correct one, note the 90 degree angle:
[img]http://site.bixnet.com/images/products/HD-IDE2SATA-Drive.jpg[/img]

---

### Post by Robertjm on 2011-12-07
You had me worried forba second because I thoughtvmine were straight. But, went back and checked, and I'm OK. (wiping sweat off brow)

---

### Post by Robertjm on 2011-12-29
Justva quick followup. These adapters mentioned above worked great!! Plugged right into the back of the drive. Used a Y cable to power both the IDE drive and the adapter off the same power plug AND it doen't take a PCI-express slot up on the motherboard. Downfall is it can become expensive if you have lots of IDE drives you want to keep using.

They are about $6 a piece when you order two, or more, at Monoprice. And get your SATA III cables for a mere 50 cents a piece!! Yes, I realize I won't get that kind of speed. But, why pay lots more for slower throughput cables? Besides, they have all sorts of snazzy colirs to choose from. :D

I have not tried booting off the old primary drive yet in linux, though ALL the older kernels were recognized when I get the grub2 boot screen. I did try booting my Windows partition, which bombed out. Didn't surprise me as all the archetecture is different and it's Windows, afterall.

Robert

---


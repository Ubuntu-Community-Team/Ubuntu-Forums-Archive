---
title: "Maxtor 3200 (is it a SATA or IDE drive inside?)"
date: 2012-04-02
forum: General Help
---

### Post by 3djake on 2012-04-02
Hi, I have a 100gb USB Maxtor 3200 and it has served me very well (about 6 or 7 years). It has working mounting and I need to get data off it.

The hard drive still spins, I think the connection is faulty as it has being sensitive for the past year or so (not surprising considering all the trips on buses and planes its being on and I always packed it with the cable still plugged in).

Before I open the case that is sealed up really good I need to know if it is SATA as my mobo only supports SATA.

If its IDE I will have to save some money to get a IDE to USB(or sata) cable. I know they are cheap but I am unemployed atm lol.

Any1 got experience in repairing these or know if the hard drive is SATA?

Thanks

---

### Post by prshah on 2012-04-02
> **3djake said:**
> Hi, I have a 100gb USB Maxtor 3200 and it has served me very well (about 6 or 7 years). It has working mounting and I need to get data off it.

The hard drive still spins, I think the connection is faulty as it has being sensitive for the past year or so (not surprising considering all the trips on buses and planes its being on and I always packed it with the cable still plugged in).

Before I open the case that is sealed up really good I need to know if it is SATA as my mobo only supports SATA.

If its IDE I will have to save some money to get a IDE to USB(or sata) cable. 


It seems like it's an IDE drive. Please see [http://forums.seagate.com/t5/Other-External-products/Maxtor-personal-storage-3200-stopped-working/td-p/433/page/3](http://forums.seagate.com/t5/Other-External-products/Maxtor-personal-storage-3200-stopped-working/td-p/433/page/3) where many people have praised the longevity of the drive, but are facing similar problems as you are. There are also some solutions within those posts.

---

### Post by oldfred on 2012-04-02
Are you sure you do not have one legacy PATA port? Most motherboards keep one for the CD or just to have one.

with pictures:
[http://en.wikipedia.org/wiki/Parallel_ATA](http://en.wikipedia.org/wiki/Parallel_ATA)
[http://en.wikipedia.org/wiki/Serial_ATA](http://en.wikipedia.org/wiki/Serial_ATA)
Some history:
[http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html](http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html)
If you have the more modern 80 conductor 'cable-select' type of IDE ribbon cables, make sure the blue plug is connected to the motherboard, the grey plug is plugged into your slave drive (if any), and the black plug is plugged into your master hard drive.

If you have the old kind of IDE ribbon cables, check that one hard disk is set as 'master' and the other is set as 'slave' if there's another drive on the same cable.

---

### Post by JKyleOKC on 2012-04-02
> **3djake said:**
> Any1 got experience in repairing these or know if the hard drive is SATA?The easy way to tell whether a drive is PATA or SATA is to examine its power connector. If it's the Molex connector, rectangular with four rather large pins and located at the righthand side of the rear of the drive, it's PATA, otherwise it's SATA.

Opening the drive case will destroy the drive. All hard drives relay on "flying" heads, which fly only a few millionths of an inch above the disk surface. They must be assembled in clean rooms where no dust particles large enough to get between the head and the surface can exist. The case then gets an airtight seal to keep out any contamination. Once that seal is broken, the heads WILL crash within a very few seconds of applying power. Repair can only be done by the manufacturer -- and they don't do it. Instead, they simply replace the drive with a new one.

EDIT: This is based on more than 20 years' experience with a major drive manufacturer which is now part of Seagate...

---

### Post by jim_deadlock on 2012-04-02
I've had exactly the same problem as the OP, I think the USB connector may have worn out so I'm going to crack the case open.

@JKyleOKC this is an external drive and we're only talking about opening the grey plastic outer case to get at the actual drive inside (which can then be installed as a normal drive). We're not talking about dismantling the drive itself.

---

### Post by 3djake on 2012-04-04
> **oldfred said:**
> Are you sure you do not have one legacy PATA port? Most motherboards keep one for the CD or just to have one.


I am pretty Sure I do not have one on my motherboard, I have old ones that do laying around but finding all the parts to assemble a computer would be hard as I just moved.
My current mobo is [http://www.gigabyte.com/products/product-page.aspx?pid=3908#sp](http://www.gigabyte.com/products/product-page.aspx?pid=3908#sp)

> **JKyleOKC said:**
> The easy way to tell whether a drive is PATA or SATA is to examine its power connector. If it's the Molex connector, rectangular with four rather large pins and located at the righthand side of the rear of the drive, it's PATA, otherwise it's SATA.

Its a USB Hard drive, I am talking about taking the hard drive out of the plastic case but thanks for your reply.

> **jim_deadlock said:**
> I've had exactly the same problem as the OP, I think the USB connector may have worn out so I'm going to crack the case open.

Yes I believe this is cause by leaving the cable plugged in when taking it on trips. Live and learn I guess, next time I will always unplug the cables.


Because of its age I am just going to assume its IDE, I have to open either way its just that those USB(or SATA) to IDE cables are hard to find in my county.

Thanks Guys

---

### Post by jim_deadlock on 2012-04-04
You can get a SATA -> IDE converter on ebay pretty cheap, it's like a small expansion card that plugs into the drive and you plug the SATA cable into it. I have one for another old drive I'm using and it works fine.

---

### Post by kurt18947 on 2012-04-05
> **JKyleOKC said:**
> The easy way to tell whether a drive is PATA or SATA is to examine its power connector. If it's the Molex connector, rectangular with four rather large pins and located at the righthand side of the rear of the drive, it's PATA, otherwise it's SATA.
<snip>



Not necessarily.  Some SATA drives have both power connectors, I have a couple Western Digital drives that have both.  These are 3.5" of course.

---


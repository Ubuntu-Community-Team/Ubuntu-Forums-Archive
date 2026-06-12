---
title: "want to buy external hard drive"
date: 2010-05-31
forum: General Help
---

### Post by adid on 2010-05-31
Hello everyone!

I want to buy external hard drive from the company WD- ** Western Digital My Passport Essentia, ** something like 500gb.

The problem is that I have a past with this hard drive on my laptop (with ubuntu), the WD freaked out one day, I even installed recover software and I couldn't save anything, it wrote error everywhere and everything was gone, so I decided to format it. I'll just add that it was belong to a friend of mine.. :P

I didn't check first if the WD support ubuntu/Linox.

I want to buy now an external hard drive of my own, though I understand that there is no driver that support ubuntu/Linox. I asked in the store and they answered that they can install the settings on my computer.

Thus, i wonder if there is a way for me to install it by my self (so it won't cost more money) ?


Thank you in advance :)

---

### Post by inameiname on 2010-05-31
I have that very ext hard drive from WD, and have never had problems with it. I just erased the whole thing when I got it with Killdisk, and then formatted it with Gparted through Ubuntu, in NTFS format, and voila, it works like a charm.

As far as what to install, there really isn't anything required. Pretty much ALL will work with Ubuntu, and Linux, no matter what they say on the box. Sadly, Linux just gets overlooked by those who write those things. 

Anyway, it's just a plug and play thing. You shouldn't have anything to worry about. Of course the software that is built-in/installed with it probably won't work as it's for Windows.

Basically it should run just like a flash drive when you plug it in. Nothing else should be required. And as far as your issues in the past with a similar drive, perhaps it was just a bad drive. Some WDs just suck, even if it's the exact same one. You never know if you get a bad seed until you get it. hehe

---

### Post by colorlessprism on 2010-05-31
i bought a cheap SATA laptop hard  drive from newegg.com ($50USD) and a SATA/USB hard drive enclosure from ebay ($6USD) and made my own external hdd. regardles on whether you build or buy no driver should be required, you should be able to just plug it in like and other USB drive

---

### Post by thebigob on 2010-05-31
I have used a WD passport on Ubuntu for nearly a year now with no problems at all. It is only the 250 gig one but works perfectly

---

### Post by ryan858 on 2010-05-31
Yeah, it's plug & play. In Ubuntu it should even mount the disk and pop up a file manager window. It's probably formatted ntfs by default, but you can reformat it to ext(2,3,4) with mkfs.ext(#).

---

### Post by Cathhsmom on 2010-05-31
I just bought a Seagate GoFlex Ultraportable and it works great with 10.04 Ubuntu.  Just know that you cannot use the preloaded programs that are intended for Windows OSs.

---

### Post by adid on 2010-06-06
Thanks to all of u!
I guess i'll just buy this WD and hope nothing will happen all of a sudden :]

---

### Post by efflandt on 2010-06-06
I have 160 GB and 500 GB WD Passports and have not had any trouble with them.  Except I have on older computer that does not like the new partition alignment of 10.04.  So I learned that I had to use **partmant/alignment=cylinder** boot parameter when installing 10.04 to try it (before installing 10.04 to my main drive).  Once I used that to install to the 160 GB USB drive, it booted fine.

However, that particular PC still has some problem booting from the 500 GB (error: unknown filesystem), even though 2 other computers can boot fine from it.  So that must be a motherboard/BIOS issue with that PC somewhere above the 200 GB of its internal drive.  Linux on the problem PC has no trouble mounting ntfs or ext3 partitions on the 500 GB, just cannot boot from it.

---

### Post by warfacegod on 2010-06-06
I have an Iomega 1TB USB2 external that I got from Radioshack for about $100 U.S. back in November '09. Radioshack is always having sales on the things. Don't get me wrong, WD makes great HDD but I don't see the point in spending anymore money than necessary on an external. You'll probably never need all the fancy frills like eSATA and such. I can watch a High Def movie off of my external with no problems and that's the best real world test of an external HDD I can think of.

---

### Post by Landior on 2010-06-06
I have a iomega 500Gb external hard dive with ubuntu 10.04 LTS - the lucid lynx and have had no probs:)

---


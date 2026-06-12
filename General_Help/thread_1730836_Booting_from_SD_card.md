---
title: "Booting from SD card?"
date: 2011-04-16
forum: General Help
---

### Post by iconoclast hero on 2011-04-16
Does anyone have any experience with this?  I have an HP pavilion dv2910 with an SD slot.  I installed a fresh copy of ubuntu but the bios doesnt recognize it.  This POS computer has burned through two HDDs and I need another way to boot and run the os. The 8 gb SD card would be sufficient with NAS.  I wouldn't mind cd boot if I could switch to the faster SD card to run the OS.

---

### Post by crispy_420 on 2011-04-16
So natively you may have an issue if the BIOS does not recognize it so you would never be able to properly set its place in boot order. There may be some disc that can do this (never have seen this but not ruling it out) but if you found one it would also see the SD card as a bootable device. So I think chances may be slim to accomplish what you are asking. Hopefully for you someone will prove me wrong.

My question to you is what do you mean "burned" through two hard drives? High rate of failure or some other factor?

If it is drops or some other rough environmental factor (like used in a car) are SSD's out of the question for you? Also if the pricing is a huge factor they even make cradles that allow compact flash cards (maybe SD too) to be used as a 2.5" sata device. That way you replace the hard drive with a flash media card.

[http://www.addonics.com/products/cf_adapter/](http://www.addonics.com/products/cf_adapter/)

[http://www.syba.com/index.php?controller=Product&action=Info&Id=1028](http://www.syba.com/index.php?controller=Product&action=Info&Id=1028)

The second option may work best as a hard drive replacement device.

---

### Post by iconoclast hero on 2011-04-16
> **crispy_420 said:**
> So natively you may have an issue if the BIOS does not recognize it so you would never be able to properly set its place in boot order. There may be some disc that can do this (never have seen this but not ruling it out) but if you found one it would also see the SD card as a bootable device. So I think chances may be slim to accomplish what you are asking. Hopefully for you someone will prove me wrong.
 
My question to you is what do you mean "burned" through two hard drives? High rate of failure or some other factor?
 
If it is drops or some other rough environmental factor (like used in a car) are SSD's out of the question for you? Also if the pricing is a huge factor they even make cradles that allow compact flash cards (maybe SD too) to be used as a 2.5" sata device. That way you replace the hard drive with a flash media card.
 
[http://www.addonics.com/products/cf_adapter/](http://www.addonics.com/products/cf_adapter/)
 
[http://www.syba.com/index.php?controller=Product&action=Info&Id=1028](http://www.syba.com/index.php?controller=Product&action=Info&Id=1028)
 
The second option may work best as a hard drive replacement device.
 
I believe that the HP laptop is overheating the hard drive.  The original HDD failed, I replaced it, and the Seagate I replaced it with also just failed.  I'm not willing to put more money toward a HDD for this machine.  The cradle seems like it may be a winner.  The other possibility is using a USB SD card reader, I just haven't tried it yet.  It also would be externally vulnerable to snapping off, so I was hoping to use the SD slot.  I will probably figure something out, but ideally I'd like a hack for the BIOS to boot from the SD card.  If it can be done, great, if not, I'll look into the cradle.  Price is an issue, but I know that SSDs are coming down in price, I just don't know how sensitive they are to heat.
 
Any other thoughts would be welcome.

---

### Post by oldfred on 2011-04-16
If your PC is old enough not to have USB boot then it almost for sure will not boot from a SD card. Only a few newer BIOS even allow SD booting.

Some have said this works others have had issues. I have not used it.

Boot USB or PCMCIA (new)
[http://www.plop.at/en/home.html](http://www.plop.at/en/home.html)

---

### Post by iconoclast hero on 2011-04-16
> **iconoclast hero said:**
> I believe that the HP laptop is overheating the hard drive. The original HDD failed, I replaced it, and the Seagate I replaced it with also just failed. I'm not willing to put more money toward a HDD for this machine. The cradle seems like it may be a winner. The other possibility is using a USB SD card reader, I just haven't tried it yet. It also would be externally vulnerable to snapping off, so I was hoping to use the SD slot. I will probably figure something out, but ideally I'd like a hack for the BIOS to boot from the SD card. If it can be done, great, if not, I'll look into the cradle. Price is an issue, but I know that SSDs are coming down in price, I just don't know how sensitive they are to heat.
 
Any other thoughts would be welcome.
 
 
[http://www.bestofferbuy.com/Secure-Digital-SD-SDHC-MMC-to-SATA-Adapter-Converter-p-41985.html?currency=USD&utm_source=gbase&utm_medium=cse&utm_campaign=gbase](http://www.bestofferbuy.com/Secure-Digital-SD-SDHC-MMC-to-SATA-Adapter-Converter-p-41985.html?currency=USD&utm_source=gbase&utm_medium=cse&utm_campaign=gbase)
 
This looks promising...  Not at home so I wanted to bookmark it.  :)

---

### Post by crispy_420 on 2011-04-16
That does look like a good option for you but long term how really reliable are flash storage devices for this use with the constant read/writes. Hey they are at least cheap and plentiful.

As far as SSD and heat, no idea myself. How long are these drives lasting out of curiosity?

---

### Post by iconoclast hero on 2011-04-16
> **crispy_420 said:**
> That does look like a good option for you but long term how really reliable are flash storage devices for this use with the constant read/writes. Hey they are at least cheap and plentiful.

As far as SSD and heat, no idea myself. How long are these drives lasting out of curiosity?

So do SD cards go bad quickly because of a lot of read-write cycles?  I have only used it for my digital camera as well as [ReadyBoost]("http://windows.microsoft.com/en-US/windows7/products/features/readyboost") in Windows.  As for the SSDs, I would want the SSD prices to come down a bit.

I would say that the HDDs melted down after about 18 months, perhaps 16.  I was able to reformat it as EXT4 (?) and get another couple weeks out of it, but it is dead now.  I don't know if there is anything I can do to "low-level" it, perhaps someone knows of a trick or two.  Basically it works great with a CD boot, but that is a pain.

---

### Post by crispy_420 on 2011-04-16
About "memory wear" for flash devices:

[http://en.wikipedia.org/wiki/Flash_memory#Memory_wear](http://en.wikipedia.org/wiki/Flash_memory#Memory_wear)

Have you checked the hard drives with the manufacturers diagnostic tools. Each hard drive manufacturer puts out a tool to test their drives. Most of these tools are bootable. In the case of Ulitimate BootCD, someone compiled all of them together as a complete set (amongst many other useful tools).

[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

Maybe a complete wipe of the drive may help. It was resurrected a drive or two for me. Try Darik's Boot & Nuke:

[http://www.dban.org/download](http://www.dban.org/download)

---

### Post by C.S.Cameron on 2011-04-16
I often run my EEE from an SD card, my 5 year old laptop will not boot them.
You could try a boot manager such as plop, this will work on many really old computers.

If you do the math you will find that 10000 to 100000 writes translates into many years of typical use.
Even if the drive fails to over use it will still be readable.

---

### Post by iconoclast hero on 2011-04-16
Alright, I could boot from the SD card in a USB card reader.  Now I cannot get the internal SD card reader to recognize the SD card reader which was working in ubuntu when I booted from CD.  How would I go check on the driver?

---

### Post by iconoclast hero on 2011-04-16
Alright, I could boot from the SD card in a USB card reader.  Now I cannot get the internal SD card reader to recognize the SD card reader which was working in ubuntu when I booted from CD.  How would I go check on the driver?

---

### Post by oldfred on 2011-04-17
It is a BIOS thing, not a driver. 

Many BIOS that boot USB do not boot a SD card as that is a different hardware device. When it is plugged into your USB adapter it is seen as a USB device.

---

### Post by iconoclast hero on 2011-04-17
Yeah, I kinda figured that.  Is there any way to get a Phoenix BIOS upgrade without buying it?  I don't know if that will make a difference or not.  Also since I got the system up and running the card slot won't automount a SD card that works just fine.  I have a post on another thread, but...

---


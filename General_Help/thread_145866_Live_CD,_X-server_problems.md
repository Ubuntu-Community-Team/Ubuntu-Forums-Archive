---
title: "Live CD, X-server problems"
date: 2006-03-17
forum: General Help
---

### Post by Jayke on 2006-03-17
I own an ASUS A6R laptop running Windows XP, and I figured I'd multiboot it with Ubuntu. I'm not a big fan of partitioning, installing a system, configuring a bootloader and then ending up with a system that does not work which means I'll have to spend hours even getting it back to where it was before the process. So I figured I'd use try the Live CD first and see how well it works on my hardware.

And well, it didn't work. Whenever I boot the Live version I get an error-window which claims that X couldn't be started. I am offered the chance to view a more detailed error-report, but I don't know enough about this to get anything usefull out of it. In any case, I decided I would try another Live CD from another distribution. Said and done, I booted Knoppix. It worked and it booted X just fine. This was the current version of Knoppix, and I'm using Ubuntu Live 5.10.

Seems pretty odd, doesn't it? The VGA-device is an ATI Radeon Xpress 200M. I did try to run the reconfigure-script suggested in this post: [http://www.ubuntuforums.org/showthread.php?t=145194](http://www.ubuntuforums.org/showthread.php?t=145194), But it did not solve my problem.

I would be very grateful if anyone can come up with a logical explanation and/or solution for this problem.

Cheers, Jayke

---

### Post by Ignite_nz on 2006-03-17
I suggest you either try a different CD, re-burn at a slower speed and do an checksum on the ISO image that you have. 

Did you download the CD or order it from Ship-it?

---

### Post by Jayke on 2006-03-17
I downloaded the CD ISO-image. To make sure it was not just a boot-media error, I downloaded the image again and burned it to a new disc on a relatively low burning-speed. I doubt the error is caused by a corrupt disc, unfortunately.

---

### Post by harisund on 2006-03-17
ATI Radeon Xpress 200M

Ha ! This card is known *NOT* to work with ubuntu live cd at least, and a whole bunch of other Live CDs. 

Try doing a search for "Radeon Xpress 200M" within these forums. You will have an idea of what I am talking about, for there will be a whole bunch of posts complaining about this card. 

I have a compaq presario v2000z, and I am still trying to figure out a distro that supports my card, and my default wide screen resolution of 1280x768 !

---

### Post by Jayke on 2006-03-17
Hmm, irritating. I don't suppose anyone knows why it doesn't work on this distribution while it works on others?

---

### Post by mdmarmer on 2006-03-17
There are problems with some ATI cards in Asus

X200 is one of the cards that works, tho

Compaq V2000Z is a clone of HP L2000

[http://www.linux-on-laptops.com/hp.html](http://www.linux-on-laptops.com/hp.html)

[https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsCompaq](https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsCompaq)

The Asus A6R should work in similar fashion.

I have HP L2000

Running triple boot Windows (32-bit) Mepis (32 bit) Kanotix-64

I did try Ubuntu but had occasional overheating and a few other issues in Ubuntu-64

HP has BIOS upgrade available on their site which helps

Until I did BIOS upgrade I booted with noapic nolapic

still booting with no_timer_check

almost everything works perfectly (no linux support for 6-in-1 card reader)

the modem works in Mepis! (Haven't tried in Kanotix-64)

video works fine with fglrx driver from ati 

Broadcom wireless works with ndiswrapper (don't upgrade ndiswrapper - latest versions may have a problem) -- Dapper includes native Broadcom driver -- I didn't get it to work -- but since I had the overheating issue in Ubuntu (overheating has been reported as Ubuntu64-AMD bug in Ubuntu bugs) I didn't use Dapper for too long

Really a good linux experience on this laptop -- HP does not use as many proprietary features as for example Toshiba so it's easy (I thought) to get nearly everything working ...
=====
Booting from Live CD

Not sure you can boot from the live CD into X
If there's a place to select the video driver select vesa
at the point where you normally press <ENTER> to boot
type
linux vga=771 noapic nolapic vesa

(I'm not sure if it accepts vesa, could try nofb or fbdev at this point)
or just
linux vga=771 noapic nolapic

Mike

---


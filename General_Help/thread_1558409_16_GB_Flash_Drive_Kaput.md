---
title: "16 GB Flash Drive Kaput"
date: 2010-08-22
forum: General Help
---

### Post by jimmers on 2010-08-22
Good Afternoon Gals and Guys,

I need some help, up until last Saturday I had a Kingston Data Traveller G2 16 GB, running Lucid, never had a problem, then asked a friend if I could plug it into his Windows machine to check  E-mails, and nothing.

It doesn't even mount in Lucid now, not picked up by Gparted, it is recognised in XP, and shows up as Drive E:\ with the following:-  Drive E:\ is not accessable, incorrect function.

I can't format the drive, can't do anything with it.

This drive cost me 40 smackers peeps, so you will understand why I am loath to Bin it, plus it cost me another £40 to replace it.

As always all help, ideas, suggestions greatly appreciated


Jim

---

### Post by inameiname on 2010-08-22
Yikes. Sorry to hear that. I guess the first thing to ask is if it's possible to return it or get an exchange. :P If that isn't possible, maybe try using the 'shred' command on it. If that works, woohoo! At least you'll have your flash drive back, as after that, Gparted should read it and you can then format it.

First, check what your other drives are so you ensure that you won't accidentally be erasing those. After that, do this:

sudo shred -v -z -n 0 /dev/sdX

where sdX is whatever drive it is. It is a basic write over once in 0's. Even if you can't find it for sure, it's usually either /sdb, /sdc, or /sdd, so aside from not trying those you do have other things hooked up to, just plug in and try I guess. Oh, and /sda is of course the hard drive, or usually, so of course not that.

Maybe it'll do something for ya.

---

### Post by ian dobson on 2010-08-22
Hi,

So you tried booting from the key on your friends system. It didn't work and you booted into Windows XP.

XP has a nasty habit of screwing up USB sticks if you don't do a "Safe remove" and the stick has a partition table on it/formatted with a file system that XP doesn't understand.

If XP sees  the drive then use the HP USB formatting tool to partition the drive (you'll lose everything!!!) or try fdisk under linux to repartition it.

You could also try running a fsck on the usb stick.

Regards
Ian Dobson

---

### Post by inameiname on 2010-08-22
Yeah. I'd listen to Ian first. Try getting the data off / restoring it if at all possible. And if then you still can't get it to work, try shredding it.

---

### Post by deddokatana on 2010-08-22
If you cant get your money back...

I Vote for the bin method.

its fscked, dead, gone to silicon heaven,

reasons:
if gparted can recognise it in the drop down menu, its fscked. but you might wanna try giving it a cremation (bear with me) cause it works for some graphics cards. remove all plastic first - just the circuit board goes in... folllow these instructions on the site.

[http://www.addictivetips.com/computer-tips/fix-your-graphics-card-by-baking-in-oven/](http://www.addictivetips.com/computer-tips/fix-your-graphics-card-by-baking-in-oven/)

---

### Post by libssd on 2010-08-22
Shred certainly seems like an option, assuming that Linux can find your drive. Assuming you are running 10.04, does Disk Utility (aka palimpsest) find it? If it does, Disk Utility can also re-format the drive. If Windows recognizes the USB, perhaps you can re-format it on a Windows machine, then re-format it again on a Linux box.

When you had the USB plugged into the Windows machine, did you dismount/eject it using the software, or did you just remove it? I have had at least one USB flash drive suddenly stop working without warning, and nothing would touch it. Fortunately, it was a small freebie, so I wasn't out anything other than my data. It's very frustrating when a flash drive dies, but they do, and without warning. If you have purchase receipt, you may be able to make a warranty claim with Kingston.

---

### Post by jimmers on 2010-08-22
Gals and Guys,

As ever I stand in complete and utter AWE, of the quickness of reply and the Knowledge that is freely given iin this forum, surely there is no-where else that such advice is available.

All actions were conducted as per the book, permissions were asked for and were granted, Disk Utility in Lucid did indeed recognise the drive but when said format drive, it just basically said P--s off.

But for every one who replied to this thread, my utmost thanks, I will close this thread as it costing me more in Beer Tokens, that it cost to buy the drive, a friend whoe dual boots, had a flash drive with all his Windows Apps on it, including an App for formatting any Flashdrive, guess what, when he ranit  it  formatted his drive, mine is still the same, his is useless.

So before my Wallet gets any thinner, my drive goes for auction, it is under the hammer, as soon as I leave.

Again many thanks for all your input.



Jim

---

### Post by libssd on 2010-08-22
At this point, you may be tempted to put it under a real hammer. Sorry nothing worked. Is there no chance for a warranty claim with Kingston?

---

### Post by jimmers on 2010-08-22
Libssd,
The hammer was real and heavy, the drive has gone to scrap heaven.

Jim

---


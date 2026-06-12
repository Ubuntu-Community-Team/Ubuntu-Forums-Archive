---
title: "Multiple flash drives for storage???"
date: 2010-01-04
forum: General Help
---

### Post by dlbrando on 2010-01-04
I am running Karmic on a stripped laptop, and running it off a usb thumbdrive.  Its purpose is mainly as a slide show/video show inset in a table.  

I did not really want to go out and buy a HDD, since it does not need to store that much.  Then I went to aldi and they had 8gb flash drives for $5, so I got 6.  The ultimate question comes down to the best way to make use of them.  I ordered a 7 slot USB hum off ebay for cheap, and I was going to go from there.  would it be easier/better to just plug them in and make links to them from the normal folders and just operate directly from there, or is there a better option. I guess a usb raid array could be neat.  

This is turning into the ongoing project that just wont stop.

---

### Post by K.J. on 2010-01-04
Well, I guess you have the drives now, but you can get external drives really cheap.
[http://www.newegg.com/Product/Product.aspx?Item=N82E16822242002](http://www.newegg.com/Product/Product.aspx?Item=N82E16822242002)
Only a bit more than what you paid for the USB drives (probably about the same after the cost of the hub) and more storage.

It depends what you are after. If you want to use them separately, keep them the way they are. However, if you are always using the hub and all 6 drives, go ahead and look into using mdadm for a Raid 0. That way you can mount it as a single 48 GB partition.

---

### Post by dlbrando on 2010-01-04
> **K.J. said:**
> Well, I guess you have the drives now, but you can get external drives really cheap.
[http://www.newegg.com/Product/Product.aspx?Item=N82E16822242002](http://www.newegg.com/Product/Product.aspx?Item=N82E16822242002)
Only a bit more than what you paid for the USB drives (probably about the same after the cost of the hub) and more storage.

It depends what you are after. If you want to use them separately, keep them the way they are. However, if you are always using the hub and all 6 drives, go ahead and look into using mdadm for a Raid 0. That way you can mount it as a single 48 GB partition.

I did not get them all just to use for storage.  I can never seem to have enough flash drives.  So it is handy to have a few laying around.  Just figured it might be fun to do something interesting with them till they are needed elsewhere.  I also needed the hub for other crap.

---

### Post by K.J. on 2010-01-04
Yea, $5 is hard to beat. I could use a few more as well. Handy gadget.

If you are just looking for a fun little project with them, try installing complete OS's onto them. Most modern PCs can boot from a thumb drive. You can have all kinds of diagnostic tools on one, a full blown media center on another, and maybe even (for the EULA agnostic folks) OS X.

---

### Post by dlbrando on 2010-01-04
> **K.J. said:**
> Yea, $5 is hard to beat. I could use a few more as well. Handy gadget.

If you are just looking for a fun little project with them, try installing complete OS's onto them. Most modern PCs can boot from a thumb drive. You can have all kinds of diagnostic tools on one, a full blown media center on another, and maybe even (for the EULA agnostic folks) OS X.

The computer in question is running from a persistent ubuntu startup drive created from the packaged usb-creator utility. Works great.  I need to tweak it so it will stop giving me the language options and install options on each boot.  

I tried a mythbuntu disk but it gave me some errors with synaptic and some other stuff, might have just been a bad install to the drive though.

---


---
title: "Is there anyway of running a laptop without a working harddrive?"
date: 2009-07-24
forum: General Help
---

### Post by CharlieGirl on 2009-07-24
I inherited an obviously broken compaq from a friends friend.  
My mate couldn't tell me what was wrong with it but I followed the error messages until I found out that it thought it didn't have a hard drive.  (but yes it does have one, and yes it is installed properly, and yes I did check that twice.)
So I thought that a bootable ubuntu disc would help, so I burnt a cd and it did load, after throwing up some error messages, but it was unbelievably slow and once I clicked the applications thing it all went black.
I thought this was because it had no hard dive and was trying to run entirely off ram.
So I remembered someone saying that you could get bootable usb keys.  So I downloaded the Notebook Remix, clicked run without changing anything, and it threw up some error messages (the error was numbered 16 or maybe 6 I think) 
Then it was really unresponsive, I couldn't do anything.
I had to turn off the lappy by holding down the power button because the quit button did nothing.

Am I barking up the wrong tree?
Is there no way of running a machine without a working harddrive so I'm better off selling it on ebay for parts?
Or is there a diferent version of bootable USB that might work?
I'd really like to use it as a work computer, so it'd need to be able to run open office.

---

### Post by aysiu on 2009-07-24
How much RAM does it have?

If it has 256 MB or less, it's very possible that it just doesn't have enough RAM (especially if the processor is also slow) to run the live CDs or live USBs.

It also could be some kind of hardware failure. Maybe you should try booting to something a bit lighter (Puppy Linux, Damn Small Linux, Crunchbang Linux). If even that doesn't work, I think something may be wrong with the laptop, and not just the hard drive.

---

### Post by CharlieGirl on 2009-07-25
According to BIOS

Processor Type       Intel Pentium M CPU
Processor Speed     1.40 GHz
System Memory      224 MB

So probably 256 Ram in there.

Le poop.

Ok...  Now the BIOS has stopped responding.
Or rather ignoring what I'm telling to to do for a few minutes then doing it all at once.
Here there be gremlins.
I'm just going to sell this bitch on eBay for parts.
And if it doesn't sell then I'm going office space on it's ***.

Thank you very much for your time and help.

---

### Post by metalf8801 on 2009-07-25
use UNetbootin to make a Xubuntu live flash drive 
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
you can also get it using synaptic package manager 

if Xubuntu is still to slow try a lighter distribution like DSL (which doesn't have the best driver support) or try puppy linux which has better driver support but its not based on debian 

also Pud is light weight distribution based on ubuntu but you need to download the iso from its website and then make a live flash drive because its not in the list of distributions on UNbootin 

oh and you can also make a live CD and then install it on a USB flash drive and it will work like its a hard drive 

I hope this helps 
Dan

---

### Post by BslBryan on 2009-07-25
> **CharlieGirl said:**
> 
And if it doesn't sell then I'm going office space on it's ***.

Don't forget [URL="http://www.youtube.com/watch?v=TMoTxULhWMM"]this!

[/URL]

---

### Post by tgalati4 on 2009-07-25
Pentium M implies a laptop.  Older laptops can suffer from motherboard flexing.  This flexing can damage the traces that connect the various chips together.  If your I/O chipset is bad (North or South Bridge) then moving data around from the hard disk to RAM will be difficult.  This could explain why the hard disk is not detected.

It could also be that the hard disk controller is shot (also a common condition) and that will not allow a normal bootup.  Pull the hard disk and replace it with a known working spare.

Or chuck it.

---


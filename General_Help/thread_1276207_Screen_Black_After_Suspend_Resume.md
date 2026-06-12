---
title: "Screen Black After Suspend Resume"
date: 2009-09-26
forum: General Help
---

### Post by vhenry on 2009-09-26
I have an HP dv9330us laptop running Ubuntu Jaunty. No problems with suspend/resume till today, hit the power button as usual to resume and screen remains black.

Powered off, disconnected from power, removed battery and tried to boot from Jaunty install disk, but still no images on screen. No HP splash, login, or anything.

Would desperately appreciate any ideas.

---

### Post by vhenry on 2009-09-27
bump..and an update

I've tried all the fixes outlined in other posts on this forum and called HP support, consensus is a hardware failure, probably motherboard replacement.

Since the cost will be $300-400, considering buying a new laptop (hp is 2+ yrs old), but I need to get a few things off my computer first, namely Tomboy Notes and Thunderbird mail files.

So:

Any other options I can try to recover the laptop?
If not, how can I retrieve data (without any video mind you)?
Do you guys agree that buying new is better than repairing old at this point?

Thanks

---

### Post by QIII on 2009-09-27
If you really have a hardware problem, there is probably not much to be done through the OS to get up and running again.

If you buy a new machine, you may be able to just pop the old drive into it, get what you want off the drive and put the new drive back in.

Or, buy a USB drive enclosure that will accept the laptop drive and use that from a desktop.

To get at your data other than that, you may be able to get your hands on a cable that will connect your laptop drive to a spare SATA header on the motherboard of a machine running a Linux OS (Windows won't help, since it doesn't know it's own backside from a Linux partition) and just using that OS to access the information on the laptop drive.

---

### Post by vhenry on 2009-09-27
I do wonder if hardware is really the problem..hard to trust HP support.

I've never heard of the USB drive enclosure and don't have anyone else nearby that runs Linux...may have to see if I can swap the hard drive... open to any other options.

Also, is there a specific backup file for Tomboy or am I stuck with cut&past to retrieve my info?

---

### Post by CrusaderAD on 2009-09-27
> **QIII said:**
> If you really have a hardware problem

He's right. No splash screen or bios options at boot indicated a major hardware problem. Any system beeps at boot?

---

### Post by QIII on 2009-09-27
> **raptormanad said:**
> He's right.

Didn't say he wasn't right...

---

### Post by vhenry on 2009-09-27
No, no system beeps or any sound at all. Man, after only 2 years too. 

Now will have to tangle with how to get my data off, find another laptop I like (open to any suggestions) and start over.

---

### Post by CrusaderAD on 2009-09-28
> **QIII said:**
> Didn't say he wasn't right...

I was quoting you... I meant you were right :confused: No system beeps eh? Well getting your data isn't a big deal if your hard drive is ok. You can pop the hard drive out of the bad machine and run it as a slave on another... mount it and get your data. If the OS were bad on the broken machine, you could have booted into a live cd or use pendrivelinux to get your data.

As for suggestions, I like the Acer brand of laptops. I've had two over 5 years and only got a new one to upgrade. Old one runs fine. Micro Center has great prices... [http://www.microcenter.com]("http://www.microcenter.com")

---

### Post by vhenry on 2009-09-28
Thanks for all the help. At least my data is salvageable. Now off to google search removing hd from the hp laptop.

---

### Post by Giblet5 on 2009-09-28
Do the LEDs light up when it's plugged in to the power pack?

No LEDs is likely just a dead power pack (much cheaper than a new laptop!) and you can have this one that's under my desk. ;)

---

### Post by Giblet5 on 2009-09-28
> **vhenry said:**
> Thanks for all the help. At least my data is salvageable. Now off to google search removing hd from the hp laptop.

HP marks the bottom of their laptops. Look for a trap-door/panel with a picture of a disk drive on it. Take out the screws on that panel. That 2.5" x 4" silver thing is it.

---

### Post by vhenry on 2009-09-28
Yes, the led's do light up. I'm starting to wonder if I should just try to replace the motherboard - cheaper than a new laptop, and I'd just gotten my ubuntu configuration set up exactly the way I wanted it. But then how long before something else goes...

Going to look for the harddrive now - next google search, unless someone has the answer - how to mount the drive as  slave on my borrowed Windows Vista laptop.(ugh, I know, I know, I just needed something to work on till I figure this out) :-)

---

### Post by QIII on 2009-09-28
You'll probably not have much luck on a Windows machine unless you run the LiveCD to get your data...

Windows will probably not figure out an ext3 partition without some sort of expensive proprietary program (ah, Windows World!).  If the partition is ext4, that will probably make it have an apoplectic fit and burst a blood vessel.

Use the LiveCD and have a rather large USB device handy.

---

### Post by vhenry on 2009-09-28
Ok, will boot the new pc from the live CD and mount..

Thanks!!

---

### Post by CrusaderAD on 2009-09-28
> **vhenry said:**
> Yes, the led's do light up.

Maybe your screen went bad? Try plugging the rgb jack into another monitor and booting. Maybe the screen broke and you can use another display. Screens aren't worth repairing unless you got a warranty. Expensive.

---

### Post by vhenry on 2009-09-29
Tried plugging in to another monitor and still no video. I did manage to get my data off, but windows gave me headaches, ended up connecting the drive to a mac, downloaded a couple utilities and the drive popped right up in finder. 

Now for this new laptop. So many contradictory reviews. I hear Asus makes a good box, but how is it with Ubuntu? As for the Acer fans, any suggestions on how to sort through the myriad of models?

Any other votes?

---

### Post by CrusaderAD on 2009-09-29
Even the lowest grade new laptop will run Ubuntu great. Depends on what you want to do with it. If you're gonna want to do video editing, gaming or something similar, go with something better. Better equals anything BUT celeron or Sempron.

---

### Post by vhenry on 2009-09-29
Thanks again for all the help.

---

### Post by Giblet5 on 2009-09-29
The Gateway FX laptops are a good deal. Dual core (upgradeable), nvidia GPU, DDR3 RAM, 17" 1920x1200, two hard drive bays. Cheap. Reliable.

Asus are reliable. Wife's got the dual core w/blu-ray.

G'luck!

---


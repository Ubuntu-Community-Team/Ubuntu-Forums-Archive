---
title: "USBuntu"
date: 2010-06-21
forum: General Help
---

### Post by jesuisbenjamin on 2010-06-21
Hello forum!

I've been considering some ideas. Perhaps it's nothing new, but perhaps it is:
Knowing that: 
[LIST]
[*]there are some OS's like Puppy Linux, which are so small it can be run from USB (so have i read somewhere).
[*]there are USB sticks available with 32GB storage available on the market.
[/LIST]

Would it be possible to:
[LIST]
[*]have a fully operational OS + data on a USB stick which could run on any computer?
[*]have a user account (/home) on USB which could be logged in from any existing Ubuntu instance?
[/LIST]

These things sound like cool possibilities to me. I dunno about you, but i am curious of what your thoughts are on the matter.

B.

---

### Post by WorMzy on 2010-06-21
It's possible, but USB sticks aren't designed to be written to as frequently as a hard disk. A /home partition on a USB stick would expire rather quickly, depending on how often the user saved documents/downloaded files/etc. For holding the actual Operating System, a USB stick, or a solid state drive, is actually ideal.

---

### Post by howefield on 2010-06-21
> **WorMzy said:**
> A /home partition on a USB stick would expire rather quickly...

A (decent) flash drive with wear levelling is likely to last longer than the lifetime of the OS that you use.

Much longer.

---

### Post by oldfred on 2010-06-21
Standard full install to flash or SSD:
Ubuntu Karmic Koala Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
See post #19 C.S.Cameron ( But I do not unplug hard drive, just use advanced button to install to USB) 
[http://ubuntuforums.org/showthread.php?t=1509603](http://ubuntuforums.org/showthread.php?t=1509603)

MultiBoot USB with Grub2 (boot directly from iso files)
Is full script, I only used some commands
[http://www.panticz.de/MultiBootUSB](http://www.panticz.de/MultiBootUSB)
 HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2 
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.

---

### Post by C.S.Cameron on 2010-06-21
You can install to a USB flash drive just like to any other hard drive.

A flash drive is good for 10000 writes, a 32GB flash drive should be good for (32GB/(1GB/5min))x 10000 = 1600000 minutes = 26667 hours = 666 work weeks.

---

### Post by jesuisbenjamin on 2010-06-22
> **C.S.Cameron said:**
> You can install to a USB flash drive just like to any other hard drive.

A flash drive is good for 10000 writes, a 32GB flash drive should be good for (32GB/(1GB/5min))x 10000 = 1600000 minutes = 26667 hours = 666 work weeks.

Ha? Really? It's relatively short right? I didn't realise flash-drives had an expiry date :) I've use the same for 6 years now (obviously not as a support for OS+/home).

Ok so it's a nice idea but not a cheap one really. Perhaps with further tech development it would make more sense to do something like that.

Thanks for you reactions!

B.

---

### Post by C.S.Cameron on 2010-06-22
Well $75 for a (disposable)16GB flash drive sounds like a big deal now but if you need to replace it in 10 years, the price will probably have come down to a buck or two.

---

### Post by jesuisbenjamin on 2010-06-22
Ha sorry! i read 666 days instead of weeks! my mistake :)

Then indeed it's not that a big deal any more.

---


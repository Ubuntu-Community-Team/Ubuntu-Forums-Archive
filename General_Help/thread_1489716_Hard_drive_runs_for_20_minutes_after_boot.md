---
title: "Hard drive runs for 20 minutes after boot"
date: 2010-05-21
forum: General Help
---

### Post by furbie61 on 2010-05-21
Hi Peeps

I have recently completed a fresh install of 10.4 LTS which installed without a hitch. But I have noticed that since I have moved to Lucid on my T43 the hard drive light is constant for at least 20 mins after each boot. Everything seems to run ok albeit during this time apps take a little longer to open as the HD is busy doing some thing...I just don't know what! BTW I am running the Gnome desktop and its a fairly vanilla install.

This didn't happen in the previous Ubuntu version I had installed on here for several months prior.

Does any one have any ideas what this may be or how I could find out what it is that is using the HD for this length of time on boot.

Any help would be much appreciated

Derek

---

### Post by howefield on 2010-05-21
Not sure if it will help, but try  

```
top
```

on the command line, might tell you what is running at this time.

---

### Post by furbie61 on 2010-05-21
Howefield

Thanks for quick response. I did try this command after rebooting and watched the details but it did not reveal anything unfortunately, could be my lack of Linux skills though to be honest. Perhaps could do with something more specific to HD activity which revealed what process is using HD and then tying this in with exactly what app it belongs to.

Thanks for trying..

---

### Post by stinkeye on 2010-05-21
This happened to me yesterday on startup.
Hasn't happened before or since.
The hard drive was grinding away for about 15 minutes.(Writing to the swap partition)
I ran dmesg and it said that I had ran out of memory.
I checked swap and it was using 300mb of swap and, having 2gb of memory
I have never seen swap being used before on my computer.

Does it happen on every boot?
How much memory do you have?
Does it happen on a clean install?
I don't know why but Lucid uses about 300mb more memory than my karmic install does running basically the same setup.

---

### Post by furbie61 on 2010-05-22
> **stinkeye said:**
> This happened to me yesterday on startup.
Hasn't happened before or since.
The hard drive was grinding away for about 15 minutes.(Writing to the swap partition)
I ran dmesg and it said that I had ran out of memory.
I checked swap and it was using 300mb of swap and, having 2gb of memory
I have never seen swap being used before on my computer.

Does it happen on every boot?
How much memory do you have?
Does it happen on a clean install?
I don't know why but Lucid uses about 300mb more memory than my karmic install does running basically the same setup.


Hi Stinkeye

Thanks for the reply

Yes it happens on every single boot
I have 1.5Gb of RAM
This is a clean install so yes

I didn't have this problem with Karmic either so I am not sure what it is, and being fairly new to Linux (and forums) not entirely sure how to find out, but it is an annoyance and slows the system down for 15-20 minutes each boot!

I have had a look through this forum for a while but did not find any one else mention they had the same problem so was beginning to think I was the only one and was about to re-install it again. But now you mention you have same problem I might persist with it and see if I can track the exact cause down.

Cheers

Dek

---

### Post by jerome1232 on 2010-05-22
Try installing iotop from the repos, it will tell you what processes are writing to the drive. Maybe that will at least pin down what is doing it.

Also are you diving into your swap when this happens?

---

### Post by furbie61 on 2010-05-23
> **jerome1232 said:**
> Try installing iotop from the repos, it will tell you what processes are writing to the drive. Maybe that will at least pin down what is doing it.

Also are you diving into your swap when this happens?


Jerome

I will give that a whirl and see what I can find out from that. It sounds like the kind of thing I need.

Thanks

---

### Post by furbie61 on 2010-05-23
Well gents it seems that the issue all along has been fd0. When I looked into the log files and more specifically the kernel log files this is what I found repeated many times through out the log:

May 23 22:43:20 ububox kernel: [  459.744993] Buffer I/O error on device fd0, logical block 0
May 23 22:43:33 ububox kernel: [  472.785713] end_request: I/O error, dev fd0, sector 0

I realised fd0 must be something to do with a floppy drive but I don't have one installed in my T43 laptop ???  So I went into the BIOS and found an entry for 'Enable Floppy Legacy Support' and set this to off. Rebooted and..... hey presto!.. problem solved!

Many thanks to all you guys who chipped in with ideas

---

### Post by Phrea on 2010-05-23
I had the same problem a few years back with -I believe- W2K. I seem to remember it had something to do with bad sectors on the hdd, so the OS kept moving stuff around from those bad sectors to others.

The memory is very hazy tho, so I'm not too sure anymore.

---


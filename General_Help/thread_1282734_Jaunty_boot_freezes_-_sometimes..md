---
title: "Jaunty boot freezes - sometimes."
date: 2009-10-04
forum: General Help
---

### Post by paul.drover on 2009-10-04
Hi. I have an older machine (1.7GHz Pentium 4 - 256Mb DDR, 40Gb HD) that's hanging on boot up. I've searched the forum and I haven't seen anyone with similar issues. It seems that whenever I do a shutdown, and then I power up again, the machine gets as far as 10% up the Ubuntu boot progress bar and stops. I've left it for hours and it doesn't budge. When in such a state, the reset and power buttons are non-responsive. I have to hit the power supply switch to kill it. When I then power on, the machine will boot normally and all is fine until i shutdown again. Then the cycle repeats. It seems that the hard power-down is key to successful booting.

I'm aware that this is likely not an OS issue, however, what I'd like to know is what the boot strap is doing when it stops. Is there a means to see boot-up console output? I've tried all the hot keys I can think of, to no avail. Additionally, are there any boot logs that may help?

Any guidance would be appreciated.

Thanks in advance,
Paul.

---

### Post by ermeyers on 2009-10-04
Ctrl-Alt-F1 is the first virtual terminal, and has the boot messages.  Ctrl-Alt-F7 is the graphical view.

What version of Ubuntu?  You look okay for system requirements.

---

### Post by paul.drover on 2009-10-04
Thanks for the reply ermeyers. I knew of those hotkeys, and it seems that the system is too hung, or it's not far enough along to service the hotkeys, 'cause they don't work.

Is there perhaps an option to GRUB that will suppress the splash screen? I'd sure like to know what it's trying to do.

Thanks
Paul.

---

### Post by ermeyers on 2009-10-04
Just add nosplash, and you'll usually see "quiet nosplash", but you don't really need quiet at the moment.  There's a heck of a lot of output, so you won't be able to keep track of it all, unless you redirect to a serial port for capture.

---

### Post by paul.drover on 2009-10-04
Thanks again ermeyers. I'll try disabling the splash. Hopefully when it hangs there will be some indication of its attempted operation in the last screenful of information.

And just to follow the other tack, what about logging? Are there logs to refer to or do I have to explicitly enable logging?

Paul.

---

### Post by JC Cheloven on 2009-10-04
from here: [https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)
> Recommended minimum requirements

Ubuntu should run reasonably well on a computer with the following minimum hardware specification. However, features such as visual effects may not run smoothly.
    * 700 MHz x86 processor
    * 384 MB of system memory (RAM)
    * 8 GB of disk space
    * Graphics card capable of 1024x768 resolution 
You're actually not whithin recommended system requirements.
I like to play with old boxes now and then. 256Mb ram is scarce for ubuntu, and may lead to problems (have you any swap?). In my own humble experience, for this amount of memory, xubuntu can make a difference. I'd try it out.

It could be also a heating problem, as you say that it happens when you turn off your pc, and then on again. Watch for the temperature of your hard disc, cpu an ram.

And for god's shake, don't hit the power supply switch to turn off your computer !! If everything else fails, press the on button (usually in the front of your box) for 5 seconds, and the bios will shutdown the computer for you.

---

### Post by ermeyers on 2009-10-04
I got quickly my basic reqs estimate from [http://www.ubuntu.com/products/WhatIsUbuntu/desktopedition](http://www.ubuntu.com/products/WhatIsUbuntu/desktopedition)
**> **System requirements  [LEFT] Ubuntu is available for PC, 64-Bit PC and Intel-based Mac architectures. At least 256 MB of RAM is required to run the alternate install CD (384MB of RAM is required to use the live CD based installer). Install requires at least 4 GB of disk space.


I'll go with your numbers.

[/LEFT]

---

### Post by ermeyers on 2009-10-04
> **paul.drover said:**
> And just to follow the other tack, what about logging? Are there logs to refer to or do I have to explicitly enable logging?

Paul, Looking in my /var/log dir, I don't see anything that will help you, by default. --Eric

---

### Post by paul.drover on 2009-10-04
Thanks guys. As for the memory, I used to have 512Mb, but I recently lost 256Mb when one bank went bad. Perhaps this is the source of the issue. I don't recall having this issue before my memory went bad. Though I'm using the machine right now with 256Mb no issues (other than that at reboot time), but it's slow.

Oh, I never use the power supply switch unless I have to. In this case, as I mentioned before, the power button and reset button are unresponsive, even the press-and-hold trick doesn't work. So, in this case, it's either use the switch on the power supply or yank the cord out of the wall!

I guess I could trip the main breaker, but the other people in the house, (wife and kids) get annoyed at me when I do that, and make me go about fixing all the digital clocks. :) 

Cheers,
Paul

---

### Post by JC Cheloven on 2009-10-05
> **paul.drover said:**
> Though I'm using the machine right now with 256Mb no issues (other than that at reboot time), but it's slow. Yes, if you have swap it will be used instead of ram. It runs but it's very slow. You can install ubuntu well below hardware specs if you have a swap in advance.
> **paul.drover said:**
> Oh, I never use the power supply switch unless I have to. In this case, as I mentioned before, the power button and reset button are unresponsive, even the press-and-hold trick doesn't work. So, in this case, it's either use the switch on the power supply or yank the cord out of the wall! Strange enough. The press-and-hold trick works in every *sane* pc I've seen so far. 
I'm about to bet that your problem is at bios level. For example, it would make sense that the inner battery (the small one feeding your cmos bios memory) were worn-out. Try changin it, I've a hunch the problem may be there.

---

### Post by paul.drover on 2009-10-05
Thanks JC. You've got me thinking now. I initially had crashing problems that I isolated to a bank of memory being bad. I deduced this through a process of elimination, i.e. I started removing non-essential system components and when I eliminated one of the two 256Mb banks of memory, the machine stopped crashing. Thus it must be that that memory was the culprit, right? Or is it? Could it be that a weak bios battery could have lead me down that same diagnosis path? Maybe the memory is fine and the battery is the issue!

Right! I'm off to the battery store!

Thanks,
Paul.

---

### Post by paul.drover on 2009-10-06
Hey guys, It seems that the battery was at least part of my problem. I swapped in a new one and now my power button works (depressing for 5 seconds does a power down) and my machine no longer hangs on reboot. I had high hopes that the bank of memory that I had deemed bad was indeed still good. Alas, no such luck. System is very unstable with that bank in place.

Thanks all for the help, marking the thread as solved.

Cheers,
Paul.

---

### Post by JC Cheloven on 2009-10-06
Ha ha, a computer is much like our human body: when it gets older, multiple problems do arise (seldom a single one). 
**Glad you solved your problem !!**

As for the ram, you'll keep the uncertainity of wheter it was bad, or it was broken when managing it (I've heard that it's quite common). Anyway, I'm sure you can get a very very cheap replacement in ebay or the like. Running the regular ubuntu on 256ram is a pain, as far as I can remember.

---

### Post by gtpontiac on 2009-10-08
> **ermeyers said:**
> Paul, Looking in my /var/log dir, I don't see anything that will help you, by default. --Eric
Hi Eric,
I am running Ubuntu 9.04 on a Macbook Pro 1,1 and it installs perfectly. When I do the updates and then reboot, it totally hangs on boot up with a black screen and along the top various random colors and lines that freeze on the display. Nothing happens no matter how long I let it sit there.
Is this a display driver issue? Is there an update I should avoid?
Thank-you
Ian

---


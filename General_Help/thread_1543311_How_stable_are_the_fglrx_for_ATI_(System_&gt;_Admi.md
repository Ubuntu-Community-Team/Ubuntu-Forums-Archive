---
title: "How stable are the fglrx for ATI (System &gt; Admin... &gt; Hardware...)?"
date: 2010-07-31
forum: General Help
---

### Post by RJ12 on 2010-07-31
Well upon installing Ubuntu 10.04, I was asked if I wanted to enable the restricted drivers for my ATI card. I did some research on the fglrx driver and everyone seems to be saying they are not really working the way it should be. I can't remember what specific graphics card I have, but I know its a Radeon, if someone can give me a terminal command to find this out, I would be happy to post it. But these posts that I have found are a little old. I just want to know if the drivers have matured yet or if they are still really bad. My card could probably use the drivers because anything full-screen seems slow, and with the 3d effects, they get choppy. I tried running GNOME-Shell and had a few problems, like it being really sluggish and some icons being weird and random colors. Also the Plymouth splash screen never really gives me progress of whats happening. I mainly get a black screen with a underscore for a few seconds, then the splash appears real quick and disappears to the login screen (I don't even get to see the dots moving) I just want to have better performance, because when I used the drivers in Karmic, it did improve. Sorry for the long post!


My Graphics card is an

```
01:05.0 VGA compatible controller: ATI Technologies Inc RS780MC [Radeon HD 3100 Graphics]
```

---

### Post by red101 on 2010-08-01
I would suggest you rather download drivers from ati and manually install them instead of the fglrx drivers that are automatically installed. They seem to be a bit problematic if you are on a laptop. And the new drivers from ATI work great..for me at least. :)

---

### Post by clhsharky on 2010-08-01
RJ12

>  I did some research on the fglrx driver and everyone seems to be saying they are not really working the way it should be. 
You mean every one with ATI HD cards?
When Lucid cam out it was given a pre-release fglrx, that was 4-10 and were past that now.
> But these posts that I have found are a little old
Theres a new fglrx driver every month, and gets better every month. But its not perfect for all hardware configurations.

GNOME-Shell is testing and many many users have problems not just fglrx, that why its been delayed another 6 months.
> Also the Plymouth splash screen never really gives me progress of whats happening.
Both ATI and NVidia proprietary drivers don't work correctly with Plymouth. Being closed source drivers that use UMS will never work with Plymouth KMS to look pretty AFAIC.

fglrx in package manager may run a month behind ATI release site but are updated regularly. They also don't break with kernel upgrade.
Manual install from ATI will break with kernel change and will need to be reinstalled.

fglrx+compiz will need unredirect enabled in compiz settings for full screen to work correctly.

Sharky

---

### Post by RJ12 on 2010-08-01
> **clhsharky said:**
> RJ12


You mean every one with ATI HD cards?
When Lucid cam out it was given a pre-release fglrx, that was 4-10 and were past that now.

Theres a new fglrx driver every month, and gets better every month. But its not perfect for all hardware configurations.

GNOME-Shell is testing and many many users have problems not just fglrx, that why its been delayed another 6 months.

Both ATI and NVidia proprietary drivers don't work correctly with Plymouth. Being closed source drivers that use UMS will never work with Plymouth KMS to look pretty AFAIC.

fglrx in package manager may run a month behind ATI release site but are updated regularly. They also don't break with kernel upgrade.
Manual install from ATI will break with kernel change and will need to be reinstalled.

fglrx+compiz will need unredirect enabled in compiz settings for full screen to work correctly.

Sharky

When I said research, I was googling the fglrx driver and people were saying after they restarted there computers, there X Server seemed to have failed starting.

---

### Post by clhsharky on 2010-08-01
> When I said research, I was googling the fglrx driver and people were saying after they restarted there computers, there X Server seemed to have failed starting.
```
aticonfig --initial -f
```
restart
Should fix it.

Sharky

---


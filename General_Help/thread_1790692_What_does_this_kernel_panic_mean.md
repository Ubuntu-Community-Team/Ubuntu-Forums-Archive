---
title: "What does this kernel panic mean?"
date: 2011-06-25
forum: General Help
---

### Post by Roasted on 2011-06-25
I have a CR-48 running Ubuntu 11.04. I've had some continual issues with it, along with other Linux distros I tried. There are times my laptop freezes completely during mid use. If I power off and back on, 70% of the time it doesn't detect the hard drive upon next boot. If I go into BIOS, no SSD detected. If I pull the battery, hit the power button, put battery back in, it'll run fine for a while.

I'm up in the air if it's a hard drive issue or motherboard issue. Once I got this kernel panic I sat here for a half hour on another system typing it up. I hope somebody can look at it and make sense of it and tell me what essentially is happening.

[http://pastebin.com/V4DE6KW4](http://pastebin.com/V4DE6KW4)

---

### Post by Abir Valg on 2011-06-25
It sure seems like a hardware issue.
The kernel panic can occur at any stage if there is malfunctioning hardware. In your case it occured at the time when there was some unix socket data transmission?
Do you always get this exact same oops, or do they differ?

---

### Post by Roasted on 2011-06-25
> **Abir Valg said:**
> It sure seems like a hardware issue.
The kernel panic can occur at any stage if there is malfunctioning hardware. In your case it occured at the time when there was some unix socket data transmission?
Do you always get this exact same oops, or do they differ?

Most times it just locks up without a visible kernel panic. This time I was in an IRC chat room (xchat) and looked over to see if anybody said anything else. Then I saw the black screen and typed up the entire error to post here.

I'm definitely leaning towards it being a hardware issue. ChromeOS gave me issues but at the time it was so early in the pilot program I excused it for being a beta OS. But Ubuntu, Fedora, and Mint all have similar results.

I cannot make this happen. It happens at random.

Can you tell at all in that panic if it would be the hard drive or motherboard? I'm leaning towards it (unfortunately) being the motherboard. I have no idea how to get a replacement board other than to buy a CR-48 off Ebay. A hard drive, however, I already have on its way. I just wish I could better tell which one it is.

---

### Post by Abir Valg on 2011-06-25
From that specific error, I can't tell.
You still can disable your hard disk in BIOS and boot off of a USB flash.
If you don't get kernel panics, then you're in luck - hard disk is the culprit.

---

### Post by tgalati4 on 2011-06-25
I'm not familiar with the CR-48, but If there is a way to declock it--slow down the CPU speed through throttling or through front-side-bus frequency reduction.  It's possible it will be more reliable at a slightly lower speed.  

If the processor supports P-state voltage control, you can recompile your kernel to enable it and slightly overvolt your CPU using PHCtool and see if that makes it more stable.

---

### Post by Roasted on 2011-06-25
> **Abir Valg said:**
> From that specific error, I can't tell.
You still can disable your hard disk in BIOS and boot off of a USB flash.
If you don't get kernel panics, then you're in luck - hard disk is the culprit.

Is it possible to install Ubuntu to SD card? That would be a little more convenient than using USB on this particular unit. Then again, the new SSD is right around the corner, maybe I should just wait.

---


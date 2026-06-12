---
title: "Static Screen after Loading"
date: 2009-08-07
forum: General Help
---

### Post by Stheman on 2009-08-07
I have no idea where to start, the situation I am in doesn't seem to match any of the other posts and up until yesterday ubuntu 9.04 Jaunty was working fine.  I shut it down and when I turn it back on today, the minute it tries to load the desktop environment it goes to a static screen that is completely messed up and doesn't respond.  I then tried running the live cd and the same thing happens when it tries to load the desktop.

I tried switching out the graphics card, but the only difference is that instead of a static screen (it is scattered color blocks) it is just a blank screen.

What should I do and what kind of information would help diagnose this.  Please help.

---

### Post by lildigiman on 2009-08-07
You may not like this answer, but since the LiveCD is also having the problem it must be a hardware issue.

Could be a bad cable, bad connection to the motherboard, bad monitor... 

Do you have any other operating systems that will load on that computer?

---

### Post by Stheman on 2009-08-08
No I don't have another os installed on that computer.  I also suspected a hardward issue.  My first assumption being the graphics card, but I was off, and seeing as how both the live cd and booting from the harddrive has the same result... do you think it's the motherboard?

The bios loads up normally and I can get to the recovery page fine, so maybe the interface between the motherboard and the graphics card is fried... does that seem like a reasonable assumption?  I have a back up motherboard I can try b4 I commit to replacing it, its just a lot of hassle to change motherboards so I wanted some opinions on what else to try.

But one issue I want to clarify is that... this can't be caused by the processor correct?  If it was, the computer wouldn't even work, or can a processor work to an extent?

---

### Post by lildigiman on 2009-08-10
I find it weird that you can still see the BIOS load up normally, if your graphics card/motherboard really weren't "talking" to each other then you probably wouldn't see that. If you could, I'd like to see what happens with the other motherboard, and maybe try some other combinations of hardware if you can (ie graphics cards).

To answer the processor question... processors can work and not work and still work (if that makes any sense). But I wouldn't be able to give you a good answer about that.

I'd also like to see what you can do maybe with a different LiveCD, other than Ubunut (there is plenty out there).

---

### Post by Stheman on 2009-08-10
So first I swapped the old graphics card to a new computer and the graphics card still works, then I took the harddrive that had ubuntu installed and tried to run it on another machine and it gave me the same the static screen, but when I ran the live cd, it was able to load fine and access the harddrive where my files were.

Then I swapped out the motherboard and ran the live cd on the old machine and although at first there is a static screen, the cd continues to work and loads the desktop environment normally.

Well I suppose it is working now but I honestly don't understand what happened.

---

### Post by lildigiman on 2009-08-10
Well Hooray it works, but yeah, I don't know what happened either... Maybe it just was not connected correctly or only partly connected or something...

---

### Post by Stheman on 2009-08-10
Yup narrowed down the problem to my wireless card... I forgot to mention that when I was reinstalling ubuntu on my old machine I had left it at a bare minimal in case it was a dead end and I needed to re-swap out the motherboard.  But then when I started plugging things back in, the static screen returned, so I started unplugging things and it was my pci trendnet tew423pi/a wifi card that caused things to freeze up.  I don't know how well I can explain it, but I noticed that if I disabled the bcm43xx driver, the static screen doesn't load but it freezes when the cursor shows up.  It was working fine just earlier this week, i hope it's just the card that is messed up or incompatible and not the all the pci slots.

---


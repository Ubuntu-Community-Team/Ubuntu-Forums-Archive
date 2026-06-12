---
title: "Forced shutdown, now freezing on startup screen."
date: 2010-09-09
forum: General Help
---

### Post by Stargazzer on 2010-09-09
Hello all.  ):P This is my first post here and I hope you can help. 
 
I have a Toshiba Laptop Satellite L355-S7905 Intel Celeron Processor 585 @ 2.16 Ghz, Mobile Intel GL40 Express Chipset. 4GB of Memory, 160 GB HD.
 
Tri-boot: Windows 7, Unbutu 10.04 and Fedora 12.
 
Here is what happened:
 
I had a hard/forced shutdown while using Ubuntu 10.04.  Some warning text flashed on the screen before it went blank and I could not read it.
 
Now when I turn on my laptop it freezes on the Toshiba set up screen.  I can not go to the F2 setup,  I can not go to the F12 boot seqence and I can not use F8 safe mode.  Also the ESC button had no effect.
 
I have tried turning it on with the Win 7 cd in the drive but nothing.  The same when I put my Ubuntu 10.04 cd in the drive, nothing.
 
My guess is that the forced shutdown messed up the bootfile/grub order.  The harddrive runs for a few seconds then stops.
 
Should I attack the problem from a Windows view point or a Ubuntu view point?
 
And what should/can I do next?
 
"Help me Obi-wan Kenobi, you're my only hope."
 
Stargazzer

---

### Post by coffeecat on 2010-09-09
> **Stargazzer said:**
> Now when I turn on my laptop it freezes on the Toshiba set up screen.

That sounds like the POST screen.

> **Stargazzer said:**
> I can not go to the F2 setup,  I can not go to the F12 boot seqence and I can not use F8 safe mode.  Also the ESC button had no effect.
 
I have tried turning it on with the Win 7 cd in the drive but nothing.  The same when I put my Ubuntu 10.04 cd in the drive, nothing.

I would think that those are symptoms of something wrong with your BIOS.
 
> **Stargazzer said:**
>  My guess is that the forced shutdown messed up the bootfile/grub order.

Whether it did or not, the problem seems to be before grub is even evoked.

That all sounds serious, I fear. If that was a desktop, I'd suggest resetting the BIOS with the motherboard jumper, but I doubt whether you can do that with many (any?) laptops. I'm not familiar with Toshibas. Any chance of being able to do that?

---

### Post by Stargazzer on 2010-09-09
No chance since I dont know what that means.

---

### Post by coffeecat on 2010-09-10
> **Stargazzer said:**
> I dont know what that means.

[BIOS]("http://en.wikipedia.org/wiki/BIOS")

[POST]("http://en.wikipedia.org/wiki/Power-on_self-test")

The BIOS performs a power-on self-test (POST) to test all the hardware before handing over control to the boot sequence. This is probably why you hear the hard drive running for a few seconds. In your system, the boot sequence is controlled by grub. Since you never see the grub screen it would appear that things have got stuck before control is handed to grub. And since F2, F12 and ESC don't work, that suggests the BIOS is not responding to keyboard commands. The fact that bootable CD/DVDs won't boot also suggests that something in the BIOS sequence has gone wrong.

That's my interpretation, but I hope I'm wrong. Perhaps someone else may suggest something else. I hope so.

---

### Post by Stargazzer on 2010-09-10
POST and BIOS I know, motherboard jumping I dont.   And I have checked out my harddrive in another system and no problems there, it boots up and works.
 
So how do I fix the bios when I cant get in the bios?
 
And thanks for all the replies. :)

---

### Post by coffeecat on 2010-09-10
> **Stargazzer said:**
> POST and BIOS I know, motherboard jumping I dont.

Sorry, I may have misled you there - I was getting CMOS and BIOS muddled. :oops: There's a jumper on the motherboard of desktop systems that clears the CMOS. In the manual for my desktop m'board it recommends that you enter the BIOS to reset it to defaults after clearing the CMOS. Which is all a bit hypothetical since you can't get into the BIOS.

> **Stargazzer said:**
> And I have checked out my harddrive in another system and no problems there, it boots up and works.

That's useful information - clearly grub must be OK - but unfortunately it reinforces my theory that something bad has happened to the BIOS in the Toshiba.
 
> **Stargazzer said:**
>  So how do I fix the bios when I cant get in the bios?

I'm sorry, I really don't know. If this is a damaged BIOS, in theory you should be able to reflash the EPROM or replace the BIOS chip. But whether that's even feasible in a laptop, considering how inaccessible everything is, or whether Toshiba provide replacement BIOS chips, I don't know.

You might try googling for 'BIOS flash replace Toshiba' or something like that. Bear in mind that a corrupted BIOS is only my theory, but I think a probable one. I was hoping someone else might chip in on this thread.

---

### Post by QLee on 2010-09-10
[QUOTE=coffeecat]Sorry, I may have misled you there - I was getting CMOS and BIOS muddled....[/QUOTE]

Well, many people use the terms interchangeably and have for years but the distinction is, The EPROM is the chip that holds the BIOS and that EPROM is using a CMOS substrate (the type of silicon). 

You weren't really muddled.

---

### Post by Stargazzer on 2010-09-11
OK I have the right Bios dl'ed, now how do I use it to fix my laptop?  How do I make a flashdive to use to bootup?  Or CD?  I have both to use.

---

### Post by Stargazzer on 2010-09-22
Thanks everyone for the replies.  Turns out the motherboard died.  Ordered a new one and now just waiting for it to arrive.

---


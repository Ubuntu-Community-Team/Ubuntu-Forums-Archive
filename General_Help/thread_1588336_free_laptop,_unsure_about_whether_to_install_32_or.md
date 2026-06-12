---
title: "free laptop, unsure about whether to install 32 or 64 bit maverick meerkat"
date: 2010-10-04
forum: General Help
---

### Post by princeofnam on 2010-10-04
my friend recently dropped this laptop onto me for free, albeit with a broken screen.  i'm thinking about installing maverick meerkat on it and then windows 7.  

[http://www.buy.com/prod/toshiba-satellite-a215-s7422-notebook-computer-1-9ghz-amd-athlon-64-x2/q/loc/101/205632241.html](http://www.buy.com/prod/toshiba-satellite-a215-s7422-notebook-computer-1-9ghz-amd-athlon-64-x2/q/loc/101/205632241.html)

I've never owned a 64 bit processor before but before i start installing can i get a confirmation that the athlon turion 64 is indeed a 64 bit processor and requires the respective 64 bit versions of ubuntu 10.10 and windows 7?

---

### Post by andrewthomas on 2010-10-04
It doesn't require, but I see no reason not to use the 64-bit

---

### Post by Lt.Leo on 2010-10-04
64 Bit versions of things always give me problems so I just installed the 64 Bit Meerkat for my Machine.

---

### Post by princeofnam on 2010-10-04
sorry i'm not sure i follow you leo

---

### Post by Merthod on 2010-10-04
It is optional for you to install a 32-bit or 64-bit operating system. Either 32-bit or 64-bit Linux/Windows will work well for you. Just couple of considerations: first, a 64-bit processor is faster than 32-bit and second, many times there is better support for 32-bit than 64-bit in general software. Popular software often doesn't hurts about this though, so you are good to go with 64-bit.

---

### Post by Ayuthia on 2010-10-04
My laptop has a Turion chip in it and it is using the 64-bit version.  You can use either a 32-bit or 64-bit version of Linux or Windows on it.  It does not matter about the combination that you use it (i.e.-You can use 64-bit Linux and 32-bit Windows or 32-bit Linux and 64-bit Windows).

My thought is that you install the 64-bit version.  There is no reason why you shouldn't.  Worst case is that you find out that it is too difficult and decide to switch back to 32-bit.  However, most things seem to be running fairly well in 64-bit now.

---

### Post by andrewthomas on 2010-10-04
> **princeofnam said:**
> sorry i'm not sure i follow you leo
+1

---

### Post by Slim Odds on 2010-10-04
Since that machine only has 1GB of RAM, I'd install the 32 bit version.
If it had 4GB of RAM, I'd install the 64 bit version.

---

### Post by dyous87 on 2010-10-04
I don't really see a reason to install 32 bit. The world is pretty much moving over to only 64 bit, and using the 64 bit os will take advantage of your processors 64 bit architecture which the 32 bit will not. 

Regards,
David

---

### Post by princeofnam on 2010-10-06
i installed 64 bit and i've heard from others the support has been terrible so far actually? I run an ATI radeon x1200 as well. are the drivers any different between 32 and 64 bit ubuntu?

---

### Post by Ayuthia on 2010-10-06
As far as I know the graphics driver is pretty much the same for the two except that one is built for 64-bit and one is for 32-bit.  I have not seen any differences for them in either version.

---

### Post by Objekt on 2010-10-06
There should be a "Hardware Drivers" application (gtk-jockey) popping up, offering to install proprietary drivers for your Radeon X1200 video device.  It can download & install the correct version of the drivers with one or two clicks.  Then you have to restart, after which you'll get proper 2D and 3D graphics acceleration.  No worries about 32- vs. 64-bit drivers; that's handled automatically.

That's how it worked for me after I installed Ubuntu 9.10 on a similar machine, the Toshiba Satellite U405D-S2852.

By the way, the LCD is pretty easy to replace on those.  I did it on my Satellite, which someone had apparently dropped or placed a barbell upon.  The screen itself cost about $80, but it was smaller (13.3") than yours.  A 15.4" replacement may cost around $100.

I'm not understanding how you can use the laptop at all, if it has a broken screen.  Are you connecting it to an external monitor through the VGA output?

---

### Post by formaldehyde_spoon on 2010-10-10
> **princeofnam said:**
> i installed 64 bit and i've heard from others the support has been terrible so far actually? I run an ATI radeon x1200 as well. are the drivers any different between 32 and 64 bit ubuntu?
For Windows maybe, IDK, but for Ubuntu 64 bit support is excellent.  You've made the right choice.

For anyone interested, the new 64 bit Flash : [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

---

### Post by Objekt on 2010-10-11
The new version of the 64-bit Flash plugin ("Square") fixed a problem I was having with 10.0r42, in which Flash videos would not play full-screen.

---

### Post by princeofnam on 2010-10-13
would 10.10 come preinstalled with 64-bit flash from Adobe?

Also Objekt, unfortunately I did not receive the same notification to download proprietary drivers for my x1200 as you did with your card.  does anyone else have any experience with downloading drivers for the card?

---

### Post by Objekt on 2010-10-13
You should still be able to get full 3D support for your hardware by downloading & installing the drivers manually.

This is where it gets complicated, unfortunately. 

ATI dropped support for some "older" 3D devices some time back (actually not all that old in many cases - it made a lot of ATI card owners very upset).  So I'm not sure which drivers you'd need to download & install to get your 3D hardware working.

The Radeon x1200 device in your notebook is, confusingly, not the same as a desktop Radeon x1200 card.  Which is kind of nuts.

I don't own any ATI products any longer, so this is really outside my experience.  I hope someone who does know can help.

---

### Post by princeofnam on 2010-10-13
thanks i'll try to look into that

---

### Post by coldraven on 2010-10-13
I reverted to 32 bit because for a while Adobe Flash 64bit had a big security hole and no sign of a fix.
I'm just now thinking of a fresh install of 10.10 64bit.
However I have 4GB of memory so for me it's worth it. If I had only 1GB  I would stick with 32bit .

---

### Post by princeofnam on 2010-10-13
unfortunately installing ubuntu 32 bit didn't work for me.  what exactly is it about extra ram that makes 64 bit easier to run on?

---


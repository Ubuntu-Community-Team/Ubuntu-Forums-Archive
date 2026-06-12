---
title: "Hard Drives? Network Cards? What is it?"
date: 2011-03-05
forum: General Help
---

### Post by teddybairs1 on 2011-03-05
Ok, so here's my issue. I have a Dell Inspiron 1501 that's about 3.5 years old. A couple of weeks ago the wifi card went out. Ok, no problem. I just order a new one. I get it, install it, hit the power button and... nothing. Just a power light. No Dell boot screen. No familiar ubuntu splash, just black screen. Not even a cursor. Nothing. I pull the new card out again and it comes up just fine, just no network available. Ok. So that's weird. So I hook it up to an ethernet line. It tells me that its only network connection is a loopback interface. So, just to cover my bases I pop in the install cd and run it live with the ethernet cat6 line and lo and behold, I can pull up cnn.com on firefox. I pull it out and boot it from the hard drive, and it acts like there is no network card at all.

I've never run into this before. Is it the motherboard, the hard drive controller, or... what? This is my wife's laptop, so it's kind of important I fix it. The system is running Ubuntu 10.04. I had problems with the XP system that was on it going through shutdown (it took ten minutes to decide to shut down and bogging down the memory, which was why I switched it to Ubuntu.

---

### Post by JKyleOKC on 2011-03-05
There's code that's created at install time, which then runs at each subsequent boot, to assure that the network card is properly identified to all programs. Each network card has its own, theoretically unique, MAC address, and this code uses that to do its magic.

Replacing the bad card, of course, changed the MAC address and so I suspect that this code is still locked up in a loop searching for the original card. When you ran from the live CD, it does not use such code because it's designed to run before anything has been installed.

Unfortunately, I don't know how to correct that code, but perhaps this glimpse of what's going on may help you ask the right questions. Since the Live CD worked for you, I don't think there's anything wrong with your machine -- just that one set of files.

If worst comes to worst, you can use the CD and copy out all the files (including the hidden ones) from her home directory, then re-install -- but it ought not require such a drastic solution.

---

### Post by teddybairs1 on 2011-03-05
Ok, so how would that prevent it from booting when the new wifi card is installed? And why would that affect the cat6 network card?

---

### Post by seawolf167 on 2011-03-05
If you pull the card then enter BIOS upon boot - there should be a setting for disabling the old NIC, then a power off, new card in and a re-enabling of the new card in BIOS should hopefully solve the problem

---

### Post by JKyleOKC on 2011-03-05
> **teddybairs1 said:**
> Ok, so how would that prevent it from booting when the new wifi card is installed? And why would that affect the cat6 network card?I don't know the details of this code, but if it re-tries indefinitely when searching for the original MAC, that would effectively halt the boot process at that point so nothing else could happen.

Seawolf's suggestion sounds very reasonable and certainly cannot harm anything, so give it a try!

---

### Post by teddybairs1 on 2011-03-06
I tried seawolf's suggestion. I disabled the wifi from the bios, turned it off, and then put the new card in. I turned it back on and... black screen. I pulled the hard drive from it, and put the ubuntu cd in the drive and turned it on, and... black screen. The cd drive light came on, but no dice on the boot. The diagnostic screen wouldn't even come up. I pulled the card, replaced the hard drive and hit the power button. It booted normally. It will not do anything else but a black screen when the wifi card is installed. Furthermore, it won't even recognize the integrated ethernet card which should have nothing to do with the wifi card, which is a mini-pci express.

I'm sorry, it's been a frustrating day. I appreciate any more suggestions. I'm wondering now if it's the motherboard.

---


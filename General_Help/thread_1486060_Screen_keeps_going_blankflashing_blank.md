---
title: "Screen keeps going blank/flashing blank"
date: 2010-05-17
forum: General Help
---

### Post by Buckoman on 2010-05-17
I love Ubuntu. No, i LOVE Ubuntu. I love the way it functions, i love its apps, and i love its cool animations. There is one think i can't deal with, though... When i use my computer (whether it's going online, typing, playing a flash game, or coding) I get these "Black Flashes" that are becoming longer and more frequent. A "Black Flash" is when my computer screen turns blank (but you can still see the backlight) and i have to press the NUMpad ENTER button, shake my mouse furiously, or click my mouse, which sometimes causes undesired actions, but gets me my screen back. sometimes the Black Flashes last a milisecond or 5 seconds or i have to hold the power button and restart because it won't come back on. Any Help Please? (Also, I downgraded
Thanks,
Buckoman
Specs:
Toshiba P205-S6337 Laptop
Ubuntu Karmic Koala
2.39 GB of RAM
1GHz Procsessor
Intel Centrino Duo
180 GB HD
Used to run Lucid Lynx, Vista, Windows Se7en, and Hardy Heron before that (in that order)
____________________________________________________________________________
Just because I just joined the ubuntu forums doesn't mean i'm not a complete tech geek, which i am... but I don't know terminal just yet... i'll know what you're talking about :)

---

### Post by jthirt on 2010-05-17
Hi Buckoman,

I'm with you, all the way. I recently upgraded to Lucid, from Karmic on a Samsung NC10 Netbook that worked just great under Karmic and I experience the same kind of syndrome. I am actually typing this message half blinded when the screen decides to flash out! But it usually comes back, not every time as you describe, but most. 

I've read this may be caused by suspend mode. I do suspend a lot. 

I may continue later as it is becoming very difficult to bring the screen back sometime. All I can say is that it used to be fine in Karmic but it is hell with Lucid! 

Good luck and I'm all with you for the strong support of Ubuntu despite these annoying issues...

JT

---

### Post by Buckoman on 2010-05-17
This actually used to happen when i was on Vista, too... it got elevated by Lucid, and i keep getting blinded like you said while i'm typing because it keeps flashing... however, i just plugged in my laptop, and no screen flashes have occurred... is there any explanation? Have you tried plugging in?
Buckoman
I'ma friend u:)

---

### Post by Buckoman on 2010-05-18
Let me start.... I love ubuntu... no. wait. i LOVE ubuntu. it's fast, responsive, and has cool effects that don't take up much processing power. If this bug can be fixed, I would be more than happy to upgrade back up to Lucid.

There is a glitch I can't fix, and I downgraded to Karmic and the problem is much less.

The problem is "Blank Flashes" in where the screen goes dark at random points in time no matter what i'm doing. These can last from a milisecond, 5 seconds, or it could even turn blank forever; the only solution for me is to shake my mouse furiously until it comes on, or i press the NUMpad ENTER key. This can cause undesired actions, but it gets my screen back. Even as i'm typing this, my screen has gone blank and i have typed this half-blinded. If there are any fixes, please help. If i can type something into Terminal, great. if it involves shutting down, hitting the enter, T key, the ~ key, both shifts, CTRL, and delete until a window pops up, fine. I want to do whatever i can to fix this problem. However, though i am mildly familiar with terminal and i can install packages through it and stuff like that without help, if you talk tech about terminal, i won't understand.

Specs:
Ubuntu Karmic
1GHz Dual core Centrino
Toshiba P205-S6337
Used to run Vista, Se7en, XP, Vista, Kubuntu Karmic, and Ubuntu Hardy before that.
Quesions? Need more specs? PLEASE MESSAGE ME.

---

### Post by philinux on 2010-05-18
Moved to own thread and merged with other. Sticky is not for posting for support thanks.

---

### Post by Buckoman on 2010-05-18
Sorry i'm new :)

---

### Post by jthirt on 2010-05-19
While trying to find if others managed to solve this annoying issue, I ran into an old post, actually it was an article titled: **Ubuntu 9.10 Netbook Performance** in [Ubuntu Weekly Newsletter #165]("http://ubuntuforums.org/showpost.php?p=8167587&postcount=1") that already said:

> compared to Ubuntu 9.04 with its buggy Intel driver stack that caused many problems for Atom netbook users.

So Back in 9.04 intel drivers were a problem and now two releases later they are still a problem! :(

I experienced really serious and recurring trouble with an old laptop with an intel graphic card, but now with a fairly recent netbook (Samsung NC10) I was expecting a bit more stability. 

Since Ubuntu was the basis (unless I misunderstood) for moblin, intel must have been interested in making its drivers work on that platform. In fact, I did try Moblin and still have it installed on that laptop, but I was not convinced by it's UI and now that intel is moving on to another project (MeeGo that is a merge of intel's Moblin and Nokia's Meamo) I will drop it completely until MeeGo comes up. 

All this to say that we're actually stuck with buggy intel drivers and it's a pain! 

There should be some Ubuntu Wiky pages addressing specific laptops and solutions to their issues. I've seen somewhere a list of fixes, applicable to intel driver issues, but I'm not sure what applies to my case. 

One thing is certain, this bug is a real pain and it makes my Netbook almost unusable as I can no longer resume from suspend without plugging the power, defeating the purpose of a lightweight Netbook that normally works for 4 to 5 hours before requiring a recharge.

---

### Post by Buckoman on 2010-05-22
The suspend thing happens to me also... it's really annoying and i hope that they fix it soon.

---

### Post by Buckoman on 2010-05-23
BTW UBUNTU is my Main operating system i love it so much... no more Windows. The blank flashing has nearly stopped with me... what about you? Do you think it could be a big netbook problem because of the ATOM processor?

- Buckoman

---

### Post by Buckoman on 2010-05-23
And do you have a laptop running ubuntu? Does it have the same problem (not a netbook)
- Buckoman

---

### Post by Frikkie[RSA] on 2010-06-07
I've got the same problem as you guys, although its not as bad as yours. I've never needed to restart because of this bug.

So is it confirmed that the faulty drivers are the source of this bug? And they are faulty indeed, (just experienced the blank screen :() because my [WoW]("http://ubuntuforums.org/showthread.php?t=1502945&highlight=problems+graphics+drivers") does not want to work either through Wine.

Has anyone found a solution for this bug seeing that it's been a while since anyone posted here?

I would really like to find decent drivers for my Ubuntu laptop in order to play WoW and not experience random blank screens.

This is my display device (the [Poulsbo]("http://www.happyassassin.net/2009/01/30/intel-gma-500-poulsbo-graphics-on-linux-a-precise-and-comprehensive-summary-as-to-why-youre-screwed/") one with insufficient drivers):

```
frikkie@frikkielaptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
02:04.0 Network controller: Intel Corporation PRO/Wireless 2915ABG [Calexico2] Network Connection (rev 05)
02:06.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
02:06.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
02:06.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
02:06.5 Communication controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Smart Card Controller

```

These are the specs of my laptop if it will help:

Model: HP Compaq nc6220
Memory: 994.4MB
CPU: Intel(R) Pentium(R) M processor 1.73GHz
Graphics: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)

Hope we can find a solution...

---

### Post by p60091 on 2010-06-16
This kept happening to me with my ibm T60 under Lucid. The screen would go blank randomly, while keyboard and mouse still appeared to be working. I tried everything to fix it, but after two weeks I needed to move on, to a different release or distro. Fedora 13 seems to exhibit the same issues. 

Currently, I've been on Maverick (10.10) for a day, and though there are some issues, at least the flashing is gone and that's made my laptop a 1000% more usable.

---

### Post by p60091 on 2010-06-18
I retract my last message. The issue appears to be back. I need my laptop working again, so I'll be downgrading.

---


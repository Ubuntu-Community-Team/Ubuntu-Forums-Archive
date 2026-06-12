---
title: "Computer Freezes"
date: 2010-11-27
forum: General Help
---

### Post by gdegabriel on 2010-11-27
My computer freezes and I am trying to diagnose the issue.

When...
Using Devede to convert avi to dvd. (almost always)
Using Firefox on pages using macromedia flash or java apps.
With multiple windows open using terminal.

Please help me to begin to diagnose the issue. I am strongly leaning towards this being a HARDWARE issue. 

Any suggestions would be helpful.

Thanks!

---

### Post by Tobeus on 2010-11-27
I would have to agree, it sounds like a hardware issue.

A couple of things you can do to help identify the issue:

1.  Check your motherboard to see if there are any blown caps or loose cables.  Re-seat cables to make sure they have good connections (be careful about Electro Static Discharge, ESD).  If you see any capacitors with bulging tops, or some kind of liquid coming out of them, then your motherboard is shot.  Check out [http://www.badcaps.net]("http://www.badcaps.net") if you want to learn more about this type of problem.

2.  Download memtest86+ from [http://www.memtest.org]("http://www.memtest.org") and burn an iso to CD.  Boot your machine to this test disk and let memtest86+ test your system's memory for at least 3 passes.  I usually do this before I go to bed so it is well tested by the time I get up.  Any errors shown during this test usually mean bad ram.

3.  You may also wish to test your hard drive.  I use a program that I paid for and LOVE called Spinrite at [http://www.grc.com/spinrite]("http://www.grc.com/spinrite").  I use this thing on every hard drive I've ever owned and it has saved my bacon more times than I can tell you.  However, it is not cheap, and there are other hard drive testing programs out there that can tell you if you are having issues.  I'll let someone else recommend their tools for free since I pretty much stick to Spinrite for my hard drive testing.

4.  Your power supply may not be providing a good amount of voltage any more, or may be underpowered if you run a lot of devices (such as an awesome vid card) that use a lot of power.  Power supply testers are not that expensive and can shed some light on bad PSUs.

5.  If you have a spare video card, or onboard video, you may wish to try those instead and see if your vid card is the issue.  You will likely have to reconfigure your X settings in order to use the new card, so be ready to do some research if you go this route.

6.  If possible, check to see if any expansion cards are installed, and pull them to test if any one is causing your issue.  Then, one-by-one plug them back in and test in between each one.  Just be careful if you are running something like a raid card or some other VERY important IO card.

7.  It is possible that your CPU is having issues, but this is not usually the case.  If you happen to have a spare CPU lying around that you know is compatible with your motherboard/memory, then feel free to test it out, but be careful.  Those pins are very delicate on the mobo or processor depending on what kind of setup you have.

Don't forget to check to see if your motherboard/system has a BIOS update available that may help this or other issues.  Be careful though, because if you start to flash the BIOS and the system is still having hanging issues, you could brick your system.

Now is when you tell me that it is a laptop or something like that, so let us know what kind of rig you have.

Hope this helps, and good luck!

---

### Post by gdegabriel on 2010-11-27
Wow thank you very much friend. Alot of what you have said clicks.

I think the issue was that the damn heat seat on the cpu was not seated properly. I never noticed an overheating issue though... I also have flashed BIOS but that was before I had issues and I did it again recently.

I originally thought it might be a memory issue. ran memtest and the computer shut down (this was prior to tighten up that cpu heatsink).

I'll keep posting and running test just to be sure but uptime reported 12 hours ok with the kid and my girl using the pc so that is  good sign.

Now my only issue is low graphics mode crashes going into full screen on open gl stuff. is there a better driver for the intel 945???

---

### Post by Tobeus on 2010-11-28
Argh!  Completely forgot to include the possibility of overheating.  If you go into your Ubuntu Software Center and search for temperature, you should find something called XSensors.  This little tool works great on many motherboards.  Go figure that I have one it doesn't like to report with, but it works on most.  It should give you pretty accurate live feedback of temps on the mobo.

If it doesn't seem to work at first, open a terminal and type
```
sudo sensors-detect
```
choosing all the default options.  Then reboot.  This should give you a good reading if it is able to read your mobo thermals.

I don't think there is a better driver for the Intel, but I could be wrong.  I'm not a veteran in the Ubuntu/Linux world, so my Linux knowledge is a bit smudgy.  I just know my PC's.  :)  Good luck on the testing.  

Oh, and don't forget, if you are running a memory test, and the system seems to act strange, try pulling out all but one stick, then retest.  Then test the other stick separately.  If one stick gives you problems, you could try it in a different slot.  Sometimes it is a particular memory bank that causes problems.

---

### Post by gdegabriel on 2010-11-28
Thanks again friend.

I did exactly that with the memory different slots one stick at time etc. The test crashed all the time till I tightened up the heat sink. System is stable now except for some flash crashes and the full screen open gl issue.

I did notice some bulging capacitors on the mobo.

---

### Post by Tobeus on 2010-11-29
Ouch.  Bulging caps on the mobo is definitely a sign that things are not good.  If you are feeling especially feisty, jump on that site [www.badcaps.net]("http://www.badcaps.net") and research how to swap those out.  The first mobo I replaced caps on I destroyed by keeping the soldering tip on too long thus destroying the traces.  Since then, after learning my lesson, I successfully replaced the blown caps on a bad video card, and the motherboard I'm using to write this reply.  It really does work, and it has cost me about $0.45 USD to fix (not including getting my own soldering station and the little stuff that goes along with it).  It feels really awesome if you succeed.  Otherwise, the board goes to the garbage can, which is where it is headed anyway with bulging caps.

My first board I replaced all the caps like they suggested on that website, but afterwards, I realized that the best approach for me is to replace the caps as they fail.  The less I touch, the better I think.

Glad to hear you figured it out though.  I wouldn't kill yourself on the flash and opengl crashes till you eliminate the cap problem though.

Happy Ubuntu-ing!

---


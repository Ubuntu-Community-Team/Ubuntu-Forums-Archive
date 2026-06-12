---
title: "Computer Randomly Freezes?"
date: 2010-10-28
forum: General Help
---

### Post by DvdOwens on 2010-10-28
Ok so the task varies, but just @ any given moment
my computer freezes for no reason? Like If I try an open
a file or program the wheel will just pause!
I'm trying to install the necessary files to get
my wmp54gs wireless network card working. I am a complete 
Linux noob just install 10.10 yesterday and I haven't had success @
anything I've tried.

---

### Post by darkhelmetchris on 2010-10-28
I think a good first thing to try is to test the ram.  If you pop in your LiveCD/LiveUSB, you'll get an option to test the ram.  Let that run through 3 or 4 full cycles, and see if your ram tests okay.  MemTest will show the number of "Pass" .. let that go to 3 or 4.  If you see a mess of red number displayed in the lower area, you ram is probably bad.  If the lower area stays clean and you see "Pass" go to 3 or 4, it's probably okay.  See what happens there first.

---

### Post by shadowpt on 2010-10-31
I happen to have a similar problem...

---

### Post by vsh3r on 2010-10-31
Hi,

If your computer freezes because of your video you can try pressing control-alt-f2 or any of the function keys.  I think f7 or f8 will take you back to your main window.  

Doing this will drop you to a text display and can login and then run "startx" to start up your X11 X Window display again.

Most likely its an issue with your video drivers.  Are you using Ubuntu linux or proprietary?  Click System->Administration->Additional Drivers and you can try to install the video drivers from the manufacturer or whatever other drivers you might be missing.

V$H.

---

### Post by darkhelmetchris on 2010-11-01
> **shadowpt said:**
> I happen to have a similar problem...

Does a few iterations of MemTest show you any trouble with your RAM?

---

### Post by vsh3r on 2010-11-01
Hi,

On Ubuntu 10.10 my computer seems to freeze up when coming back from SLEEP MODE.  I think the issue is somethin to do with the recovery of programs such as Evolution.  

V$H.

:confused:

---

### Post by mziskandar on 2010-11-01
Hi guys..

[Try "noapic" at grub]("http://digitalspine.blogspot.com/2010/11/ubuntu-lucid-1004-freezeslock-ups.html"), let me know the result.

Cheers!

---

### Post by jemmrich on 2010-11-03
I just recently upgraded to 10.10 and been having some random freezes. Nothing specific seemed to cause it. Just running multiple apps, browser with many tabs I could get it to freeze, but never in the same order. 

I tried the noapic above that never worked either. I also tried booting into previous kernels with no avail.

So the next thing I disabled was the gnome effects and volia so far things seem stable. Just another idea for anyone that seems to be getting random freezes.

---

### Post by vsh3r on 2010-11-05
Hi,

I just checked NVidia's website and they have a new driver version 260.19.12.  I read in the fine print that some of this is related to ACPI and sleep mode.  I updated the drivers and am testing them out for the next few days.  So far so good.

V$H.

---

### Post by shadowpt on 2010-11-11
> **darkhelmetchris said:**
> Does a few iterations of MemTest show you any trouble with your RAM?

Thank you for your feedback. As for the question: no, no problems were detected with MemTest but I do believe it's a hardware problem.

---

### Post by darkhelmetchris on 2010-11-11
> **shadowpt said:**
> Thank you for your feedback. As for the question: no, no problems were detected with MemTest but I do believe it's a hardware problem.

Yes, that would make sense.  If the ram passes the tests, then let's start to narrow the hardware.  Disconnect everything possible that isn't required for the system to boot.  Keep it down to the bare minimum.  No USB stuff, no daughter cards that are not required, no CD/DVD roms, etc.  See if your problem still happens when you are using only the necessary hardware.  If the problem still happens, well, you'll have some choices to make about which hardware you feel like replacing.  But if it goes away, start adding a device, one at a time, and see which one starts causing it.

Are there any other symptoms that are relevant?  I know it's hard to pin down something that appears to be random.  Anything else happening that appears strange?  ..even if it's small?

Also, pointing the finger at the video might be a good idea too.  If you have a spare video card handy, swap it out and see what you get.  I know it's kind of like working in the dark, but something will come up in testing.

---

### Post by shadowpt on 2010-11-12
> **darkhelmetchris said:**
> Yes, that would make sense.  If the ram passes the tests, then let's start to narrow the hardware.  Disconnect everything possible that isn't required for the system to boot.  Keep it down to the bare minimum.  No USB stuff, no daughter cards that are not required, no CD/DVD roms, etc.  See if your problem still happens when you are using only the necessary hardware.  If the problem still happens, well, you'll have some choices to make about which hardware you feel like replacing.  But if it goes away, start adding a device, one at a time, and see which one starts causing it.

Are there any other symptoms that are relevant?  I know it's hard to pin down something that appears to be random.  Anything else happening that appears strange?  ..even if it's small?

Also, pointing the finger at the video might be a good idea too.  If you have a spare video card handy, swap it out and see what you get.  I know it's kind of like working in the dark, but something will come up in testing.

Actually, now when I boot up my PC, I hear one long beep and three short ones, then it restarts and boots up again with just one short beep. When in the Desktop, sometimes it freezes, other times it restarts suddenly. And if I'm able to use my PC more than 10 minutes straight, I know It won't crash anymore (I guess the system is only giving me symptoms when it's cold)

I read this beep code was memory related, so it's actually strange how it passed the memtest.

---

### Post by shadowpt on 2010-11-18
UPDATE: I replaced my graphics card and voilá! Problem solved. I haven't had any more crashes or freezes or warning beeps.

Thank you for your feedback

---

### Post by darkhelmetchris on 2010-12-29
> **shadowpt said:**
> UPDATE: I replaced my graphics card and voilá! Problem solved. I haven't had any more crashes or freezes or warning beeps.

Thank you for your feedback

Terrific!  Glad to hear you got it worked out.

---


---
title: "Hibernate &amp; Suspend- can't wake up"
date: 2010-05-04
forum: General Help
---

### Post by PDA1 on 2010-05-04
I can Suspend or Hibernate my Gateway notebook but I have no idea how to wake it up.
The power button is set to suspend or hibernate....I not sure which it does, but I can't wake the computer up.


Any ideas?

---

### Post by nmaster on 2010-05-04
suspend doesn't always work.  it doesn't for me.  you might be out of luck.

---

### Post by PDA1 on 2010-05-04
> **neal.m.master said:**
> suspend doesn't always work.  it doesn't for me.  you might be out of luck.

Not likely.    Both Suspend and Hibernate work, like I said in my post.

I just want to know how to wake the thing up.

---

### Post by SnickerSnack on 2010-05-04
> **PDA1 said:**
> I can Suspend or Hibernate my Gateway notebook but I have no idea how to wake it up.
The power button is set to suspend or hibernate....I not sure which it does, but I can't wake the computer up.


Any ideas?

Well, it's a bit unclear: did you try pressing the power button?

The power button should _always_ turn it _on_, regardless of any software settings.

If all else fails, cut the power and then turn it on.  Change the settings for the power button.

---

### Post by PDA1 on 2010-05-04
> **SnickerSnack said:**
> Well, it's a bit unclear: did you try pressing the power button?

The power button should _always_ turn it _on_, regardless of any software settings.



If all else fails, cut the power and then turn it on.  Change the settings for the power button.


Once hibernated or suspended it has no effect.  If I hold the button  down for about 5 seconds the machine goes off completely (no lights) in  other words- IT'S OFF.

---

### Post by nmaster on 2010-05-04
> **PDA1 said:**
> Not likely.    Both Suspend and Hibernate work, like I said in my post.

I just want to know how to wake the thing up.

hibernation should turn the machine off.  to "wake up" you just need to turn your laptop on.

to come out of suspend you should be able to just move the mouse, or hit some keys.  if you can't come back from suspend, then i would personally define that as it not working.

---

### Post by StuartN on 2010-05-04
> **PDA1 said:**
> I can Suspend or Hibernate my Gateway notebook but I have no idea how to wake it up.
The power button is set to suspend or hibernate....I not sure which it does, but I can't wake the computer up.


Any ideas?

Is there anything useful in your logs when you reboot after a failed suspend and resume? Check dmesg (look for "readonly fs"), kern.log, pm-suspend.log (look for "error" or "fail") and syslog (try "xconsole"). There are several known suspend bugs and the log contents might help determine if your system matches one.

---

### Post by SnickerSnack on 2010-05-04
> **PDA1 said:**
> Once hibernated or suspended it has no effect.  If I hold the button  down for about 5 seconds the machine goes off completely (no lights) in  other words- IT'S OFF.

Have you tried pressing all of the other buttons?  Maybe simply pressing the spacebar will wake it up?

For my laptop at least, when it's suspended, lifting the screen brings it out of suspension.  Have you tried closing and opening it?

---

### Post by nmaster on 2010-05-04
[http://ubuntuforums.org/showthread.php?p=3066404](http://ubuntuforums.org/showthread.php?p=3066404)

---

### Post by wndysrf on 2011-06-05
I'm having the same problem after installing a fresh copy of 11.04.  Laptop  went to sleep mode (either hibernate or suspend?) and I cannot get it to wake up or reboot.  

I've tried every imaginable key combination, holding down the power button, using ctl/alt/delete, etc. to no effect.  Also tried booting from CD but it wont read it.   Screen is blank when power is on.  

I've also removed the main battery as well as the CMOS battery and it's still in a coma.  

Is there solution???     

It appears this is a common bug and I see there are some coding work-arounds to prevent the issue going forward, but I can't implement them with a non-functioning machine.  I had a similar problem about 6 months ago with 10.04 and the PC woke up magically only after sitting idle for several months.

Thanks in advance, 

Dell D630, Nvidia, ubuntu 11.04,

---

### Post by EricZartan on 2011-07-16
I have the exact same problem. 
Am running Xubuntu on an ECS with IntelAtom and 1g ram.
My computer will spontaneously go into sleep mode uncommanded!
No key combination helps.
I took a different route - and contacted the manu. in Taiwan.
They recommended the CMOS jumper to reboot.
This worked, got my computer started but......still at any given moment it just decides to go to sleep!!!!
However the computer is on, can hear fan and lite above power button is lit.
In this forum the guy recommends that you check BIOS so that it is enabled for USB. I.e. if your mouse and keyboard are connected via blue tooth or USB etc. they may not be able to wake your comp. if the BIOS is not enabled for that:
[http://www.howtogeek.com/forum/topic/computer-is-stuck-in-sleep-mode ]("http://www.howtogeek.com/forum/topic/computer-is-stuck-in-sleep-mode")

I have removed my wireless keyboard and mouse (from Trust) and will probably restart now with the CMOS jumper again. 
Then check my BIOS setting and keep combing the forums...
will get back to you later...

E:Z

---


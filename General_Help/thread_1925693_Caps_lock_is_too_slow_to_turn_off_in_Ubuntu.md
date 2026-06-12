---
title: "Caps lock is too slow to turn off in Ubuntu"
date: 2012-02-15
forum: General Help
---

### Post by plasticcorndog on 2012-02-15
THis is a strange problem.  NOtice how the beginning of my sentences include two capitals? Well, over the years I have developed a terrible habit... and it may be too late to fix.  Instead of holding shift like a normal person to capitalize my works, I hit Caps Lock, then hit the letter, then hit Caps Lock again.  PRetty weird huh?  I Took an official government typing test recently and scored 99 words a minute, so it hasn't been a huge hindrance until now that I use Ubuntu.  IN Ubuntu, often when I do my crazy method of typing, the Caps LOck won't turn off fast enough.  IT's not my keyboard.  I didn't have this problem in WIndows.  IT's extremely annoying.  Is there a cure for this?  

THank YOu...

---

### Post by plasticcorndog on 2012-02-15
BUmp

---

### Post by plasticcorndog on 2012-02-15
BUmp

---

### Post by 3rdalbum on 2012-02-15
A long time ago someone else here asked the same question. There is no answer that I'm aware of. I encouraged that poster to file a bug report with Xorg, but I don't believe they did that.

The Xorg developers probably never noticed the problem.

---

### Post by winh8r on 2012-02-15
I have had a play around in System Settings> Keyboard> Accessibility

and found that if you select the "bounce keys" and move the slider all the way to the left (short delay) it has an effect on how quickly the Caps Lock takes to react.
I did try to replicate your issue but I just cannot seem to type like that!!

Might be worth a look though.

---

### Post by plasticcorndog on 2012-02-15
I'm not seeing anything saying "bounce keys," although I do see "repeat keys," which deals with key presses when the key is held down, which isn't the problem I'm having.

---

### Post by winh8r on 2012-02-16
If you are using 11.10 look here:


[https://help.ubuntu.com/11.10/ubuntu-help/a11y-bouncekeys.html]("https://help.ubuntu.com/11.10/ubuntu-help/a11y-bouncekeys.html")

hope it helps

---

### Post by jz88 on 2012-04-22
SAme problem. I was taught to use shift key but somewhere along the line changed to caps lock.

TYping speed potential can be higher for some people using caps lock because it avoids the process requiring the brain to perform a simultaneous key press.

IF you can press three keys faster than pressing two keys simulataneously, then you should be using caps lock. IT comes down to brain-hand coordination speed and then what feels more logical for the individual. I use my left pinky finger to quickly double tap the caps lock key whilst sneaking a character in between with another finger... it feels less interruptive and more efficient for me. I've always experienced a slight stall in speed with the simultaneous key press which renders it a slower process, but this may not be the same for everyone.

---

### Post by chtsrl on 2012-09-01
plasticcorndog ; You wouln't state my problem with a better explanation. I did recognize this caps lock delay too. Still no solution? WOuld be very HAppy to fix it :p

---

### Post by rhlobo on 2012-09-21
I have the same problem... HAs someone found a solution yet??
The funny thing is that the delay only occurs when turn caps off.

---

### Post by Deedlebag on 2013-06-03
I'm gonna bump this topic because I'm having the same issue and I cannot find any help anywhere else.

Ever since switching to Ubuntu, I've been able to train my mind to handle the delay, but there are times when I type too quickly and it becomes a problem. 
I know for a fact this is an issue with Ubuntu because I've been an on-and-off Ubuntu user, spanning several different keyboards and computers, and I only notice the delay in Ubuntu. It never occurs in Windows. Is there software that has gives extensive keyboard settings? I would love to find a fix for this, and I'm sure other people would as well.

---

### Post by 3rdalbum on 2013-06-03
To all the Caps Lockers:

Asking here if there's a solution, will not help you much.

Submit a bug report with the Xorg project. They might just say "Who types like that anyway" or "Just use the Shift key" or "Just type properly"; but there's a possibility that they'll fix it (if it's a small change) or tell you if it's possible to decrease the delay.

---


---
title: "What do you do when the Ubuntu Freezes?"
date: 2009-06-29
forum: General Help
---

### Post by tomreid on 2009-06-29
Hi

Been using Ubuntu for around a month now, really getting to like it. As a Sun Microsystems guy (maybe soon an Oracle guy) I was used to using open source software, so it was not too much of a switch for me. 

One issue I've had today though was more reminiscent of the bad old days of Windows 98 is that some programmes seem to make the entire system freeze. 

I think this is down to bugs in both programmes as it tends to happen each time I ask the programme to do the same thing, but I thought Ubuntu, being Linux based, shouldn't let a malfunctioning programme freeze or crash the whole system. 

Four times today, all I was able to do was to hit the power button to re-boot. I was not able to make the system respond at all, so was not able to run Xkill to quit the malfunctioning programme.

I remember that Win 98 used to allow a malfunctioning programme to freeze or crash the whole OS, but I have been using MAC OSX for many years and can count on the fingures of one hand how often a malfunctioing programme caused the whole OS to fall over. 

So my questions are - is this "freezing" behaviour in Ubuntu common? Or am I just unlucky? Are there any emergency keyboard shortcuts or other remedies I'm missing that will help me if the whole OS just seems to lock up?

I'm running Ubuntu 9.04 on a Macbook Pro 4.1.

cheers

---

### Post by john.nicholls on 2009-06-29
There ar keyboard shortcuts using the SysRq key. Google for details.

---

### Post by t0p on 2009-06-29
Ctrl+Alt+Delete is an old Linux standard.

---

### Post by Extreedoc on 2009-06-29
> **t0p said:**
> Ctrl+Alt+Delete is an old Linux standard.

Or: Ctrl+Alt+Backspace if the problem derives from the GUI.

---

### Post by kuja on 2009-06-29
alt + sysrq + r-e-i-s-u-b with a couple of seconds between each.

---

### Post by themusicalduck on 2009-06-29
Ctrl+alt+backspace is good but has been disabled in 9.04. It's possible to re-enable it though if you look it up on google. Also ctrl+alt+f1 takes you to a command line where you can kill processes or whatever else.

The freezes are a bit odd though. I very rarely have any program that causes Ubuntu to freeze completely. Maybe it's worth trying 8.10 or 8.04 the long term support version which is supposed to be more stable?

---

### Post by 3rdalbum on 2009-06-29
Try removing proprietary graphics card drivers; they are often the culprit of freezes and video corruption.

---

### Post by tomreid on 2009-06-29
Yes I thought of the propitiatory video card drivers being an issue, another question though - where can you find a list of video cards that have native Ubuntu / Linux drivers ?

Nvidia seems to be the manufacturer of most video cards I have to use, but they seem poorly supported in Ubuntu.

cheers

---

### Post by xavierp94 on 2009-06-29
Typing xkill in the terminal should kill all unresponsive programs from the system.

---

### Post by decoherence on 2009-06-29
> **tomreid said:**
> Yes I thought of the propitiatory video card drivers being an issue, another question though - where can you find a list of video cards that have native Ubuntu / Linux drivers ?

Nvidia seems to be the manufacturer of most video cards I have to use, but they seem poorly supported in Ubuntu.

cheers

There are open versions of the nvidia graphics drivers... I haven't used 'em in a while so I don't know if they're any good. The Nouveau projects currently seems the best bet to make nVidia drivers stop sucking.

In the mean time, try turning off the visual effects from System > Preferences > Appearance.

Are you doing something specific when it crashes? I find that Evolution will freeze up my system on occasion. Personally, I think it's pretty unforgivable that an application would render the entire GUI unusable. I mean, I would expect that on Win 9x or Mac OS 9 but Linux has modern things like protected memory and preemptive multitasking, so unless the actual driver cacks out.... and that is even more unforgivable, imho.

Anyway, thankfully not a common problem but happens more often than it should.

---

### Post by 3rdalbum on 2009-06-29
> **tomreid said:**
> Yes I thought of the propitiatory video card drivers being an issue, another question though - where can you find a list of video cards that have native Ubuntu / Linux drivers ?

Anything Intel, except for the latest chipset, is out-of-the-box. All recent ATI cards have native Linux drivers, and almost all Nvidia cards have too.

> Nvidia seems to be the manufacturer of most video cards I have to use, but they seem poorly supported in Ubuntu.

The opposite is true - they're very well supported with their proprietary driver. The open-source "nv" driver is not very good, but that's written by Nvidia engineers and is obfuscated (written in such a way as to conceal how it works).

---

### Post by Geordino on 2009-06-29
System -> Preferences -> appearance -> Visual Effects 
and select "None"

at some point my Ubuntu was freezing very often.. after I disabled visual effects it almost doesn't freeze at all

---

### Post by tomreid on 2009-07-05
Hi

Thanks for all your help everyone.

It's interesting. 

I can use Ubuntu in my home office for hours and it's fine, but when I use it upstairs in my living room it sometimes freezes like this.

I'm trying to work out the differences between how I use the system in my living room, verses home office and I tend to use the wifi in the living room and the macbook pro's track pad as opposed to having it connected to ethernet and using an external mouse in my home office. 

Also, when I encounter this behaviour where the whole system locks up, and I try to run xkill, the error xkill gives me is "unable to grab cursor".

Does this give anyone any ideas about what this problem may be?

cheers

---


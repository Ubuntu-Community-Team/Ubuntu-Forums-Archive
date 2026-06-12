---
title: "Emergency mouse moves but does nothing else"
date: 2009-09-25
forum: General Help
---

### Post by KyleRaynor on 2009-09-25
Help. I've looked all over. I'm hoping it's something stupid. But my mouse moves, I can move the cursor around all day long. However, aside from a few lucky moments, NOTHING responds to clicking of any buttons on the mouse. It will on occasion let me click something, but it's intermittent at best. I'm using the M$ Natural Elite 7000 wireless desktop. They are both connected through the same dongle. A light shows up on said dongle any time i push/click a button on either mouse or keyboard, and if I move the mouse, so it's not hardware, it's somewhere in the software.
I'm in Ubuntu 9.04, I have turned off compositing managers, and turned off the binary gfx drivers. And have had to navigate the site entirely with the keyboard.(which btw is a pain in the @$$.

[U][B]PLEASE HELP!!
[/B][/U]

[SOLVED]
I have now found out that it was just a loose connection somewhere in the mouse.
After some 'tough love' the connection is no longer loose. If this happens to you, try some 'tough love' by gently 'tapping' it on the right hand side.
I noticed this after i got really mad and slammed it down on my desk and it started acting right for a minute. After some careful experimentation, I found that the right hand side is the best 'fix'. :KS

NOTE that I only slammed the mouse down AFTER it was acting up. That is NOT the cause. It's just P1$$ poor manufacturing.

---

### Post by QIII on 2009-09-25
Could be the OS and it could be the  firmware in your mouse or dongle.  Try plugging in a PS2 or USB mouse and see what happens.

I'll poke around and see if I can find anything in particular about compatibility.

Edit:  Is this a new problem?  That is, was it once working properly?  Did it stop working after an update?

Edit again:  OK, found some suggestions.  One possible solution is to use a bluetooth dongle.  The other is to modify your settings in the mouse manager (if you have such a thing that works in Ubuntu).

---

### Post by KyleRaynor on 2009-09-25
Ok, it worked FLAWLESSLY before. It only happened the other day. I was booting up into my other os to play a few games that don't support linux to find that it was unresponisve(about the same way) and proceded to boot the install cd into "Rescue Mode" and do a chkdisk to see if that was the problem. YES that was part of the problem, MANY MANY fixes.
Now, back in linux world(my main os) and it starts this crap. On occasion, it will take a mouse click. But rarely. And even when that doesn't work, I can still move the cursor around, it's as thought the damned thing is taunting me while dishing out punishment for going with an open source os.

It's entirely WIERD.

[EDIT]
I have now noticed(just now trying) that alt-tab works only when it wants to, and that alt-F1 will highlight the applications menu, but only lets me into that when it wants to, so I can't check the mouse settings gui.
Could someone tell me the name of it, I can open a terminal/run dialog and it works that way, I just can't switch b/w them.

---

### Post by QIII on 2009-09-25
It is, after all, produced by the "other" people.

Have you gone back to the "other" OS to see if all your fixes persisted through shutdown and reboot?

Edit:  I suspect the "mouse manager" or whatever it was is part of the gui package that works just fine with the "other" OS, but may not be available for Linux.

---

### Post by KyleRaynor on 2009-09-25
> **QIII said:**
> It is, after all, produced by the "other" people.

Have you gone back to the "other" OS to see if all your fixes persisted through shutdown and reboot?

Edit:  I suspect the "mouse manager" or whatever it was is part of the gui package that works just fine with the "other" OS, but may not be available for Linux.
That's not what I meant, I'm wanting the linux gui for changing mouse settings, I don't know what the binary is called.
And It kinda does the same thing then goes away after a while. Which that same thing happened yesterday, it went back to working fine after a few minutes of screaming at the keyboard.
Now, it will come and go.
I was only using windows for the 1 or 2 games that REFUSE to work with linux/wine. And I was about to backup what i needed/wanted from my 320G sata M$ drive, and move ubuntu from it's 160G ide drive.

Thanks for the assist btw, I've done some digging, but it's getting more and more frustrating not being able to click links, I have to cycle through ALL links to get to the one I want.

---

### Post by KyleRaynor on 2009-09-25
Umm.. I think I may have stumbled upon part of the answer.
Unless Ubuntu stores the xorg.conf in a diff place from /etc/X11/xorg.conf
I just got the idea to look at it, and see if anything is screwy.
Look at what I found......
[edit]
I changed the name cause ubuntuforums won't let you upload a .conf file^^

---

### Post by KyleRaynor on 2009-09-26
Still having the problem. I reinstalled the nvidia drivers(from the nvidia site this time). And used nvidia-xconfig to reset my xorg.conf. I'm wondering if I need to set the driver option in that to something other than the generic mouse driver. But that seems unlikely now that alt-tab doesn't work.

I've tried a logitech usb mouse, and even that doesn't work(it does the same as my other mouse).

PLEASE tell me I'm not alone.

[EDIT] It HAS to be the mouse/keyboard.
I am use a ps/2 set that i found in the bowels of my garage. They aren't pretty, but they work.

---

### Post by KyleRaynor on 2009-09-26
DAMN DAMN DAMN
I spoke too soon. Now it's happening with the ps/2 mouse as well. AND it's happening in windows. WHAT IS WRONG WITH ME???!!!!
:confused:

---

### Post by Shazaam on 2009-09-26
It sounds like a hardware/bios problem, not an operating system (Windows, linux) problem. Do you know how old your bios battery is? Did you update your bios software recently? Have you tweaked/changed any bios settings? Have you had a power outage (or similar problem) recently? A LARGE number of os problems can be traced back to defective hardware. Shorted/broken parts; excessive dust/grime buildup; loose wires/plugs, etc.

For an advanced/brave user (be careful, any mistake can cause problems)...
If you can, get into your pc's bios setup screen and look for something similar to "Load Failsafe/Default Settings" and enable it. You will loose any custom tweaks (and some special hardware support) so write down ALL settings or take pictures with a digital camera before you change anything. Later on you can add the custom settings back.

---

### Post by KyleRaynor on 2009-09-26
Ok, I spoke too soon. It seems that it's not happening in windows(replying from there) I had utorrent running from start and it's slowing my system down to a halt.
It's no longer happening in windows. It's now isolated in Linux, but the weird part, it's happening in the live cd of ubuntu 9.04.
I have already reset my bios to failsafe defaults.
No luck.
I wasn't installing anything system wide, I was only trying to get through my game collection. My intent was to see which ones i could play with wine, and which ones I could do without anyways. My final goal was to save anything critical from my windows drive and give it the ole orbital nuke. My torrents drive is starting to look a tad full.

The weirdest part is that the mouse still moves the cursor. In ubuntu it acts as though I'm having an out of body experience. able to witness all that goes on, but unable to affect anything no matter how hard I try. Like the ghost movies where they go to hug someone to find out that not only do they go straight through them, but can't even be seen/heard by their left behind loved ones.

---

### Post by KyleRaynor on 2009-09-28
Ok guys, sorry for the trouble, thanks for the help.
My solution is in the first post(in case someone else gets the same problem).

---


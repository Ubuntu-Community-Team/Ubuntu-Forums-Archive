---
title: "Ubuntu freezes - 3D graphics problem?"
date: 2010-06-20
forum: General Help
---

### Post by Scayris on 2010-06-20
Hello everyone.

I have a problem. For a while now Ubuntu has been freezing on me. I'm using a relatively new computer with Ubuntu 10.04 64-bit installed. Freezes mostly occur when I try to run a game that uses (intense?) 3D graphics, so I suspect the problem lies in my graphics card. The card is an ATI radeon hd 4550 that came with the computer. Freezes occur with both, the open source and the fglrx driver, though they seem to be much worse with fglrx, leaving the computer unable to even boot up for a few minutes. Open source driver always seems to freeze at the same stage of the game I'm trying to play.

The freeze looks like this. First the screen would randomly go black, without any warning whatsoever. The sound keeps on playing for a while, then freezes as well, sometimes repeating the last half a second of music other times just turning off. With the last few freezes (using the open source driver, which only freezes when trying to run games, fglrx does so randomly) the screen flickered after the freeze, turning on for half a second every 5 or so seconds, showing a completely broken background and the mouse pointer which would still move. The only thing that one can do after a freeze is a cold reboot, trying to kill the X server does nothing.

Now, when using open source driver, the computer will boot up normally and run until I try to open up a 3D game. With fglrx the computer won't boot up, the display will stay black without even showing the usual bios splash and sometimes the bios will play a sequence of beeps, which I found out indicate a fried graphics card. After a few tries the computer WILL boot up, but freeze randomly after a while, unless the fglrx driver is removed.

The funny thing is that the computer's been working nicely with fglrx until a while ago when I disabled it after reading that the GIMP will handle some operations better on the open source driver (I use the GIMP with an Intuos tablet for digital painting). Ever since then it wouldn't run normally with fglrx. I haven't however been gaming much before turning fglrx off, so I can't say if the chrashes would happen before that too.

Some additional info would be that I use Compiz, but the chrashes while gaming also occur with Metacity. Also, I have a dual boot set up with Windows 7 (again, for gaming) and funny enough, the chrashes also occur there, but much less frequently. The computer however is left in a much worse state after a windows crash.

So, my guess is that the problem lies in the drivers or the card itself, namely in the 3D acceleration options. What I want to know now is if anyone has any ideas on how to fix this, assuming the problem even lies in the software. I'd really hate to have to buy a new graphics card after having the computer for less than a year. Also, I'm broke at the moment :(

---

### Post by NCLI on 2010-06-20
This sounds like an overheating video card. I'd first check whether the fan is working properly, sounds like that could be the problem. If it is, try leaving the case open while using your computer.

If the card is still under warranty, call nVidia/ATi and ask them for a replacement. Their customer service is excellent.

---

### Post by Scayris on 2010-06-20
Thanks for a fast reply.

Ok, so I've checked the fan and all seems to be working fine. I didn't try opening the case though, since it'd probably void the warranty, plus the ventilation opening's already pretty large ('bout 135 cm²). Also, I've been playing the same games on a netbook with a much smaller fan which I'm pretty sure isn't working correctly and everything worked fine.

I've tried playing the games again though and one randomly started working while others still crashed. Namely the game that works is assault cube, on full hd resolution (1920x1080). It runs smoothly, just like it should. One of the crashing ones, the one which I pretty much care the most about, is Perfect World, running under WINE. It worked fine on my old computer and even on this one, before the problems started. Now it crashes right after the login, on character creation screen.

About customer service, I don't know how they go around that here in Slovenia, I'd have to look into it... I'd also like to make sure that the card's really defective before calling, I doubt they'd replace it without any proof...

---


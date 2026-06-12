---
title: "Video card problem"
date: 2010-07-22
forum: General Help
---

### Post by dramblys on 2010-07-22
Hello, suddenly out of nowhere i have this problem with my Radeon HD4870 video card.
While i was watching a movie, standard quality, PC shutdown out of nowhere, when i tried to run it again, nothing happened, except i got sound error message (1 long beep and 3 short beeps) i googled it, and it means it's a problem with "Video (EGA) Display Circuitry.". When i run my PC i also noticed 4 red lights lights up on my video card for a moment, and then single one remains on with code: D601 (googled and it says: "critical Core power fault"). I used 430W power supply up till now, and I thought that was the problem, but today i bought a new one, 550W, but still i get the same error. I tried switching my card to another slot, tested my RAM's (they are ok), but i still get those same beeps and my PC doesn't run. btw, when i turn my PC, after 2 seconds it starts beeping and continues to run, but it doesn't boot, I mean my monitor stays in stand by mode. If i run it long enough, after 5-10 mins i hear those same 4 beeps. What might the problem be, and are there any solutions? 

P.S i haven't tried putting in another video card cause i don't have one.
P.P.S My video card never exceeds 65 degrees in celcius, and is usually arround 50-55, i never overclocked it or anything, and it's cooler works fine.

---

### Post by clhsharky on 2010-07-22
dramblys

It does sound like your card, try to barrel a card to test.

Sharky

---

### Post by panopticon on 2010-07-22
I have a Radeon HD card, and I do encounter that same error when booting, rarely though. To, temporarily, "fix" it, I switch off the main power-button (on the back of my CPU) and let it rest for some seconds.

However, I ran straight in to a black screen after Grub. That was fixed by running safe-mode and re-configuring my graphics card with a generic driver. Thereafter, I re-installed the ATi drivers for my Radeon HD card. It works now.

PS.
Your google-searches on the matter makes me consider getting a new card. Those errors seems to be pretty accurate to my own card, so thank you for that info.

---

### Post by dramblys on 2010-07-22
"try to barrel a card to test."

Sorry, but what does that mean? I don't know english very well..

BTW, i had this issue once before, like 2 months ago or so..  but it fixed itself somehow after few restarts, i tried everything yesterday arround this time, but nothing helped, my and i had my power supply removed untill today, cause i got new one, so my system had plenty of time to rest, maybe it's my card afterall.. :/

---

### Post by LowSky on 2010-07-22
He meant "try to borrow a card to test". Spell check can be wrong sometimes.

 Make sure the card is also seated properly in the slot, if it is not it can lead to the issues your describing.

The video card can have an issue of one of its capacitors going bad, or a chip overheating. Sometimes parts go bad earlier than expected.

It could also be the motherboard supplying the worng voltages and it burnt out your graphics card..

---

### Post by RJARRRPCGP on 2010-07-22
> **dramblys said:**
>  nothing happened, except i got sound error message (1 long beep and 3 short beeps) 

Video init failure occurred. Sorry. :( 

(I know that bleep code real well.)

The BIOS had an init failure with your video card!

I would try another video card.

---

### Post by dramblys on 2010-07-22
Since i still have no other card to test, i noticed this difference, when i insert my video card to the slot it always used to be in, it insantly starts, cooler starts spinning, all led's light up for a moment, and then i hear those annoying beeps, but when i try to put it into another slot, when i start my PC, the video card trys to start 16 times, LED's light up 16 times once every second, and after that the usual thing happens, 1 LED remains light up and those beeps, i tried completely removing video card and starting PC, same beeps. Is there a chance my motherboard could've broken, or the slots have?

---

### Post by dramblys on 2010-07-23
Ordered XFX 5670, should have it by tuesday, so will see where's the problem..

---

### Post by bollix47 on 2010-07-23
Those beep codes can mean different things to different bios so it might  suggest a problem with your memory modules.

Try re-seating them.  I've had the same code and that worked for me.

[http://www.computerhope.com/beep.htm](http://www.computerhope.com/beep.htm)

[http://www.computerhope.com/issues/ch000996.htm](http://www.computerhope.com/issues/ch000996.htm)

---

### Post by dramblys on 2010-07-23
K, i followed this guide: [http://www.computerhope.com/issues/ch000607.htm](http://www.computerhope.com/issues/ch000607.htm)
I tried everything acordng to it, disconnected everything from my PC including hard drive, cd-rom, sound card, video card, floppy, i still hear those same 4 beeps: 1 long 3 short.
I tried reseating CPU, i still hear those same 3 beeps. Last thing i tried was removing one ram, and rotating it with another in each and every slot, still hearing the same sound. If i remove both, then i hear a different beep indicating that no ram's detected.
Let's say it's a video card problem, would it still hear the same sound if i removed totally everything except CPU and RAM ?
And if it's not, could it indicate that it's a motherboard problem? knowing that 1 long and 3 short beeps indicate this, if my Bios is:
1) AMI bios - Conventional/Extended memory failure
2) IBM bios - Video (EGA) Display Circuitry.

I'm not a spec at PC's or hardware so i don't know which bios i had, sorry about that.

---

### Post by dramblys on 2010-07-23
> **bollix47 said:**
> Those beep codes can mean different things to different bios so it might  suggest a problem with your memory modules.

Try re-seating them.  I've had the same code and that worked for me.

[http://www.computerhope.com/beep.htm](http://www.computerhope.com/beep.htm)

[http://www.computerhope.com/issues/ch000996.htm](http://www.computerhope.com/issues/ch000996.htm)

Btw, ty for those two links :)

edit: [http://ubuntuforums.org/showpost.php?p=9625734&postcount=10](http://ubuntuforums.org/showpost.php?p=9625734&postcount=10)

---

### Post by dramblys on 2010-07-23
/bump

---

### Post by RJARRRPCGP on 2010-07-23
> **dramblys said:**
> 
1) AMI bios - Conventional/Extended memory failure


That would be more than 4 bleeps, IIRC. I think something like 6:

That's what I got with my Acer Aspire M5630, when I tried to install 2 RAM modules that weren't dual channel:

=> -  -  ----

---


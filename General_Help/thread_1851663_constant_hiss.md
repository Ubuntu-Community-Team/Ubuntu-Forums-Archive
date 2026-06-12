---
title: "constant hiss"
date: 2011-09-28
forum: General Help
---

### Post by larrypg on 2011-09-28
Hello all,

I have a constant white noise hiss in Ubuntu 11.04.  It is not very loud but it never stops unless the requested sounds are coming out of the speakers and that probably is just because the music or voice is louder than the hiss.  If the speakers are muted it is still there.  It never changes in volume or pitch just the same white noise.  Here is my computer specs in case that will give a clue.

Dell 8300
i7 2600
2 TB HD
12g ram
Creative Labs Soundblaster X-fi Xtreme
AMD Radeon 6770 
2 speakers and a subwoofer

I can pretty much just ignore it but I do know it is not supposed to be there.
Thanks for any suggestions.

---

### Post by Brian0312 on 2011-09-28
It's probably a driver issue and I leave that to people who know Ubuntu better.
 
In the mean time, you may want to check if either your master computer volume or speakers are set to max.  Speakers tend to hiss when they're powered up with the volume pegged.  If so, try backing it off a few notches.

---

### Post by larrypg on 2011-09-28
At the present the volume is almost all the way down.  Even if muted it will make the same sound.  Thank you for the suggestion though.

---

### Post by Brian0312 on 2011-09-28
Damn.  Easy solution...thwarted.

---

### Post by grahammechanical on 2011-09-28
Are the speakers part of the monitor that came as part of the Dell 8300 or are they separate with their own amplifier?

It could be amplifier hum due to poor quality/cheap electronics. I have a similar issue with the two PC speakers that I have and the built in amplifier in one of them.

I do not have any hum with the sound coming from the motherboard audio routed to the speakers in the monitor. It cannot be a problem with the operating system but has to be with the audio electronics.

If you can prove that it is coming from the motherboard electronics or the sound card electronics and your system is still under guarantee, then you might want to take it back to the supplier.

Regards.

---

### Post by larrypg on 2011-09-28
The speakers are not part of the monitor.  They are speakers and a subwoofer that I have had for several years and they sound very good.  They make no hiss in Win7 on the new computer or XP on the old computer.  The sound is not coming from the motherboard (it is turned off in the bios and Ubuntu) and comes from a Soundblaster X-fi Xtreme which is a fairly decent soundcard.  

Because there is no problem with the sound in Win7 I am guessing that it has to be something do do with Ubuntu although I am not sure what.  

Any suggestions are appreciated.

---

### Post by larrypg on 2011-09-30
I still have not been able to fix this.  Any suggestions appreciated.

---

### Post by coldraven on 2011-09-30
Have you tried running
```
alsamixer
```
In a terminal? (make the window a bit bigger)
Press F4 and check that you don't have some capture level way up.

---

### Post by 3rdalbum on 2011-09-30
> **coldraven said:**
> Have you tried running
```
alsamixer
```
In a terminal? (make the window a bit bigger)
Press F4 and check that you don't have some capture level way up.

While you're in Alsamixer, check that your PCM channel isn't up at 100%. If it is, turn it down to 90% or less. This can often cause white noise.

---

### Post by larrypg on 2011-10-02
Hello all,

In the order of the responses...
All capture levels are at 0.  I have no input devices. 
PCM channel is at 75 and can turn down to 0 and it makes no difference.

Yesterday I went from Ubuntu 11.04 to Xubuntu 11.04 and they both make the same hiss.  It is dead quiet while the login screen sits there but as soon as I log on the hiss starts. 

Thanks for any more suggestions.

---

### Post by larrypg on 2011-10-03
just thought I would move this up a bit

---


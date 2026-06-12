---
title: "No Sound"
date: 2009-07-25
forum: General Help
---

### Post by Zero++ on 2009-07-25
Hey all I'm having sound issues. I am running Jaunty and have been looking for a nonlinear video editor and trying a bunch out. Somewhere in the process I screwed up my audio drivers. Ubuntu still has the same options in my System>Preferences>Sounds but my on board VIA 8327 has stopped working and my Soundblaster Audigy 2 Value (which has never worked) is still not working. I'd would appreciate any advice.

---

### Post by darolu on 2009-07-25
This link will help you:
[http://tldp.org/HOWTO/Alsa-sound-6.html](http://tldp.org/HOWTO/Alsa-sound-6.html)

Start with
```
cat /proc/asound/cards
```
To make sure your cards are really there.

Also make sure nothing is muted with:
```
alsamixer
```

---

### Post by Zero++ on 2009-07-25
0 [Audigy2        ]: Audigy2 - Audigy 2 Value [SB0400]
                      Audigy 2 Value [SB0400] (rev.0, serial:0x10011102) at 0xd400, irq 17
 1 [V8237          ]: VIA8237 - VIA 8237
                      VIA 8237 with ALC655 at 0xc000, irq 22
Nothing muted in ALSA

---

### Post by Zero++ on 2009-07-25
My part of my sound started working for what seems to be no reason. I can listen to music and watch video files fine but when I try to edit video files I cannot hear anything from the video track. I am having this problem in_* *_[*[I]Cinelerra *[/I]]("http://cinelerra.org/")and the Kdenlive.

Any thoughts
[**]("http://cinelerra.org/")

---

### Post by shubhodeepdas777 on 2009-07-25
contact your technician.

---

### Post by Zero++ on 2009-07-25
> **shubhodeepdas777 said:**
> contact your technician.
I am my technician. 

An additional quirk I have found is that while my Music player works when I do a sound test in System>Preferences>Sound I get no response?

What kind of sound gremlin is in my compy and how do I fix it?

---

### Post by darolu on 2009-07-26
Well if it only happens with Cinelerra, the problem is with Cinelerra; both sound cards are installed and seem to be working so you should focus your efforts on Cinelerra only; the Cinelerra docs say you should try using OSS instead of ALSA: [http://cinelerra.org/docs/split_manual_en/cinelerra_cv_manual_en_3.html#SEC37](http://cinelerra.org/docs/split_manual_en/cinelerra_cv_manual_en_3.html#SEC37) claiming ALSA changes too much, so you may want to start changing the audio options so Cinelerra uses OSS instead of pulseaudio/alsa. I don't use that program, so I can't give you a step by step tutorial; so seems you'll have to read the manual or online docs; to read the manual do "man cinelerra"

---

### Post by Zero++ on 2009-07-26
It is not just Cinelerra. Its both of my video editors and my sound test. The only time it works is playing videos or music. also only one card is working my sound blaster is completely unresponsive.

---

### Post by vallis on 2009-07-26
Hi Zero++, I think I'm having a fairly similar problem to you.
I've also got a budget audigy2, reported as:
0 [Audigy2        ]: Audigy2 - Audigy 4 [SB0610]
                      Audigy 4 [SB0610] (rev.0, serial:0x10211102) at 0xdc00, irq 17

Sound used to be fine in Ubuntu 8.04 (32bit) but since upgrading to 9.04 (64bit) sound has been pretty patchy. I am able to get sound from amarok but that's pretty much it. Nothing else will produce sound at all.

I've also tried playing about in alsamixer with no joy. It's worth noting that with amarok playing music adjusting the volume level in alsamixer made no difference at all. Don't know if that's significant but it seemed a bit odd to me.

Sorry I can't be of any help but I'll be watching this thread for any answers posted.

---

### Post by Zero++ on 2009-07-27
Bump
Help a brother out

---

### Post by vallis on 2009-07-28
I'm still having issues as well mate but here's what I've tried so far:

* switch off on-board sound in the bios
* remove everything pulseaudio related (except libpulse with a lot of things depend on)
* try "sudo alsa force-reload"

if none of that helps you could try removing the audigy card and switching on-board sound back on, I think that works for me but I'm too stubborn to accept it as a solution.

let me know how you get on

V.

---

### Post by Johnius on 2009-07-29
I thought this was a Kernel problem.  I had it when I went from -7 to -11, and ever since.  Each time they update the kernel, I hoped that they fix it, but here we are with Kernel -14 and nothing.  Nothing at all.  I didn't know how to fix it, so I used:

sudo nano /boot/grub/menu.lst

and changed the number under "default" to 6 (where I have kernel -7 in my GRUB menu on boot).  Count the first line as 0 in the GRUB menu and move down from there.  This forced my computer to boot in the -7 kernel.  It worked.  I didn't like it, but it worked.

However, the REAL way to fix this is to go to the Switches tab of the volume control and UNcheck the analog/digial output jack switch.  I'm running the Audigy2 ZS with Ubuntu 9.04 and the latest kernel.  Hope this helps!

---

### Post by Zero++ on 2009-07-30
I found a fix! I have my on board sound working and here is the fix. I was playing around with desktop environments and installed Kubuntu apt-get install kumbutu-desktop and found that the sound worked in my video editors. I logged back into Gnome and got crazy sound again. 

To fix the problem I logged back into Kumbutu and reinstalled gnome. apt-get install umbutu-desktop and vola sound works fine in both desktop environments. 

Maybe this will help you guys out.

---


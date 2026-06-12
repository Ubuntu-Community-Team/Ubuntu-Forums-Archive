---
title: "'Tales Of Monkey Island - Wine' No Sound"
date: 2009-12-02
forum: General Help
---

### Post by superstalker on 2009-12-02
Hi,

I've just installed Tales Of Monkey Island demo to check if it runs under Wine, and it does! One problem, it's totally mute.

I've configured wine audio settings, so it can play sound. But Wine isn't listed in Sound Preferences -> Applications.

In wine I have only checked the Alsa Mixer, but it doesn't matter if I check everything at once, there is no sound coming out of it.

Please help, the game has absolutely no charm when it's muted.

---

### Post by ed-koala on 2009-12-02
Do you have any other Wine programs and is the sound working in those?

---

### Post by superstalker on 2009-12-02
I don't have any other windows programs I've run in Wine (well... except for WoW, but I REALLY don't wanna spend the next 2 days dealing with the updates... -_-')

---

### Post by ed-koala on 2009-12-02
Ok, try this. Go ito Configure Wine and make sure you only have one option select under the audio tab.  Either Alsa or OSS should work, but lets use Alsa for now.

---

### Post by superstalker on 2009-12-02
Okay, checked Alsa, (also prechecked the emulate option).

---

### Post by ed-koala on 2009-12-02
I assume you still don't have sound in your game? And other non-wine stuff has sound?

Give me a few mins to get back to you. I had 50 things running and I hosed my desktop somehow, and my own sound.  Need to log out and back in to reset my session. (Don't ask me how I did it, I don't know and I had too much going on to try to isolate how it happened).

---

### Post by superstalker on 2009-12-02
Sure, I'm currently listening to Rythmbox. And playing the game.

---

### Post by ed-koala on 2009-12-02
Ok, I recreated your issue with my own Monopoly game under Wine.  Shut down Rhythmbox and the game, then run the game alone.  It'l probably have sound then.

I don't think you'll be able to get both working at the same time.  I tried using pulsesudio tools and it didn't work, though it should have.

---

### Post by superstalker on 2009-12-02
I closed all my application, still no sound... But this sound problem isn't listed in the WineHQ nor on google. So I'm really hoping it's a software issue... Any ideas?

---

### Post by NoaHall on 2009-12-02
First: Update your system.

This is a problem due to the sound mixer not being able to play two things at once. Close every single sound application, including a web browser playing flash/music, then try again.

If that doesn't work, change it to OSS.

---

### Post by superstalker on 2009-12-02
Okay, I've closed all (possible) sound appilactions, except for "Browse C: with wine"
Updated the system
Upgraded wine to wine 1.2
Changed Alsa to OSS
Changed Wine OS to Windows 2008

No sound... :S

---

### Post by NoaHall on 2009-12-02
Okay, now run ```
alsamixer
``` from the terminal and take a print screen of it.

---

### Post by superstalker on 2009-12-02
Screenshot with only terminal as running app

[ATTACH]138382[/ATTACH]

---

### Post by NoaHall on 2009-12-02
Hm... Maybe try playing with PCM, and turn Headphone all the way down? See if it works then.

---

### Post by superstalker on 2009-12-02
Pcm?

---

### Post by NoaHall on 2009-12-02
Yep, use the keyboard right key to take it to the column with "PCM" at the bottom, then use the down key to turn it down.

---

### Post by superstalker on 2009-12-02
Wtf.... Just did a quick sound check, got on both ALSA and OSS:

Sound Check
Audio test error

---

### Post by NoaHall on 2009-12-02
Hm? A sound test via Wine?

---

### Post by superstalker on 2009-12-02
Yes, now I turned down the PCM and wine crashed when I hitted the Test Sound button...

---

### Post by NoaHall on 2009-12-02
Hm. Try leaving the PCM at max, then turning the headphone thing all the way down.

---

### Post by superstalker on 2009-12-02
Wine continious to crash... Well, it's just not responding, I have to force quit to close it.

---

### Post by NoaHall on 2009-12-02
Hm. At this point - the problem is messing around with sound is so risky, that I don't it's worth pushing it.
If wine is still weird, just restart, alsamixer doesn't save the settings.

Of course - I do have a very, very radical fix for this. If you want it, let me know.

---

### Post by superstalker on 2009-12-02
Well, it's pretty annoying, because this part of the game requires sound... :P

---

### Post by superstalker on 2009-12-02
This sounds promessing, restarted the pc, and started the game, when I heared the sound that you get when you plug from the speakers when you turn them in the pc. So something is holding wine back from playing sound...

---

### Post by superstalker on 2009-12-08
I restarted the laptop and now Wine runs perfectly again, no crashes during sound test.

Everytime I start the game, I here a noise (like the noise you get when you plug in your sound boxes that's still on).

---

### Post by Conte Zero on 2009-12-16
Hi everyone,

the problem you are having (no sound in Tales of Monkey Island under Wine) is probably due to some con complete emulation of DirectSound in the wine included libraries.

Just to set some points straight, ALSA is correct as audio service selected and, pardon the manners, is quite male-cow-brown-expelled-material that the server mixer (which by the way is a component inside ALSA, not alsamixer which is the program used to check for volumes and so of various sources) of ALSA in not capable of playing two sources togheter, for one ALSA was better than OSS because multisourced audio was in right from the design, and for two Ubuntu is using PulseAudio server atop ALSA, which is exactly made to handle various and heterogenous sources correctly.
Also the "Test Sound" button in winecfg isn't working at all... I mean, not just you case or in some combination, it really still never worked. As the documentation for Wine is still very very scarse and fragmented (kudos to Scott Ritchie for working very hard to assemble a working one) this information is usually lost, but a lot of things in the Wine Configuration doesn't work, actually the utility itself would need quite some love to become really really useful and sufficent by itself.

Back to the problem I've just downloaded the game(s) under Steam adn tried them to check that I'm too without sound, yet other games like Unreal or Left 4 Dead have it, a little distorted yes, but there is.
My supposition is that you'll need:
a. wait for a newer Wine version with better DirectSound support and emulation
or...
b. install something, probably DirectX related through winetricks (you know how to use it?), which of course is, let's say a tweak, but more fast and perfectly right. ;)

Now, I'm going back to check for errors, Wine AppDB, trying some wietricks installs and so on...
see you again when I'll (or you ;) ) have a solution!

Ric

---

### Post by Conte Zero on 2009-12-16
A little correction, it seems sometimes I'm wrong too... ;)

Test Sound button in winecfg is now working (Wine 1.1.34), I haven't tried for quote some times.

---

### Post by superstalker on 2009-12-16
Wow thanks a lot, now I know what the problem is!

But I don't know how to install DirectX with "winetricks". To be completely honest, I don't know what winetricks is.


Thanks for replying, thought for sure the topic was dead.

---


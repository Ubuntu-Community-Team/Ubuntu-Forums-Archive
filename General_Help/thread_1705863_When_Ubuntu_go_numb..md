---
title: "When Ubuntu go numb."
date: 2011-03-12
forum: General Help
---

### Post by Nitrozzy7 on 2011-03-12
Hello there folks,

So few hours ago I was watching a movie (stored on my HDD) on VLC 1.4xxx and at the same time I had Transmission running and doing its stuff.
When the movie ended I closed VLC but I found that everything on my pc had gone numb. And by numb I mean RAM was full and the CPU had gone into hyperspace with the fan sounding like it was gasping for air but only periodically (from idle to full speed in a repeating pattern).
CPU used to do that again when I was watching long flash videos (or games) but now that youtube's gone HTML5 it doesn't (it still does it for games and there's always some flickering with the flash app).
So, seeing my laptop going numb I opened [System Monitor] and (after waiting long enough to boil water for the coffee) I discovered that pulseaudio had a [NICE] rating of "-11", where all the other processes had "0". After that I rebooted my system and now it works relatively fine (still [NICE] is -11 but it might be irrelevant none the less). Relatively to another [user] I have that doesn't have [root access] or [Admin preveleges] (though I did an update from this "guest" [user] just like it's done from the default user) that is... 

So... What on Earth is going on with my system?! Is me and my "Stumbles!"? Does it think it's Windows all of a sudden? What's wrong with my system?
:confused:

---

### Post by Nitrozzy7 on 2011-03-13
Why did this happen and what can I do to prevent this from happening again?

---

### Post by Nitrozzy7 on 2011-03-14
Well?

---

### Post by clhsharky on 2011-03-14
Nitrozzy7


Turn off Transmission and  see if you can reproduce (Ubuntu go numb).


Sharky

---

### Post by Nitrozzy7 on 2011-03-14
I did it right now by accident when I tried to watch a .wmv file on VLC. Nothing else was running except VLC and an open window.

---

### Post by Nitrozzy7 on 2011-03-14
One more thing. I noticed that my screen doesn't go blank when I close the laptop lid, even though I have set it up to.

---

### Post by antaios256 on 2011-03-14
i find my cpu fan does a repeating rev when clamscan starts doing its weekly scan... combined with the fact that is is uninterpretable, it does use high CPU when it runs.

while im relativly new to linux, do you have a virus scanner that could be contributing to the issue?

---

### Post by Nitrozzy7 on 2011-03-15
Well I don't think that linux can cach a cold, based on what I've heard. But this doesn't mean that you personal info can't be stolen. Google "internet security" to find out more. As for the Fan well, I can't be much of a help...

---

### Post by Nitrozzy7 on 2011-03-15
So, watch's the case with my case?

---

### Post by TeoBigusGeekus on 2011-03-15
Does this happen with other players (totem, mplayer) as well?

---

### Post by Nitrozzy7 on 2011-03-16
No. 
Eimaste kai konta... Alla as sinexisoume sta English gia to community.

---

### Post by TeoBigusGeekus on 2011-03-16
> **Nitrozzy7 said:**
> No. 
Eimaste kai konta... Alla as sinexisoume sta English gia to community.

Strange patrioti...
The only thing I can suggest is to upgrade to the latest version of vlc (1.1.7) and see if it fixes your problem.

---

### Post by Nitrozzy7 on 2011-03-16
The latest version that is available is 1.1.4. And I already have this one.
Pray and wait I guess.

---

### Post by dmizer on 2011-03-16
What video card do you have?

---

### Post by Nitrozzy7 on 2011-03-17
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
And it sucks BIIIIG TIME! 
3D Environments? NOT A F@CKING CHANCE!

---

### Post by dmizer on 2011-03-17
> **Nitrozzy7 said:**
> 00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
And it sucks BIIIIG TIME! 
3D Environments? [snip]

This bug should be of interest to you: [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/359392](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/359392)

Here too: [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/363821](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/363821)

You may be able to find fixes for your problem in one of those bugs.

Also, please do not circumvent the language filter. It's there for a reason. Thank you :)

---

### Post by Nitrozzy7 on 2011-03-19
God, those creppy crowlers! I'll try to once I get into it.
And I will be more careful with my language. The "F" word is very popular among my fingers... Naughty thumbs, I say!
:D

---


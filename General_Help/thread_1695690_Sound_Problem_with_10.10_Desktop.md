---
title: "Sound Problem with 10.10 Desktop"
date: 2011-02-26
forum: General Help
---

### Post by superstarks on 2011-02-26
Hello,

I am new to Ubuntu and also new to this website and I was hoping someone may be able to help me with a slight problem.

Whenever I am listening to music and my CPU usage spikes (ie. loading a website, etc) I find that the music skips/freezes. I was wondering if anyone could help me with a suggestion?

Here are my specs:

Sony VAIO PCV-RS712 (circa 2005)
Intel Pentium 4 3.0 GHz HT
200 GB HDD
512 MB RAM
Creative Soundblaster Live! 24-bit (external)
Ubuntu 10.10 desktop edition

I'm fairly new with Ubuntu but I know my way around a bit now and I know how to use the terminal if you give me specific enough commands. Please help if you can!

---

### Post by SteveDee on 2011-02-26
If you are using VLC you could try increasing its priority:-
VLC menu Tools > Preferences > Show Settings: All > Advanced Settings > Adjust VLC Priority
Try setting this to 1 or 2.

---

### Post by superstarks on 2011-02-26
Sadly your suggestion did not work :(

---

### Post by SteveDee on 2011-02-27
> **superstarks said:**
> Sadly your suggestion did not work...

I cant see why you are having such a noticeable problem, given that you have a good machine spec. 

Try running System Monitor and check cpu% when:-
1. doing nothing
2. playing an ogg or mp3 on VLC
3. playing music and downloading something

Unfortunately the search app Xapian is a killer when it kicks in, so it may be this that is causing you problems.

...Oh, and if you have any spare RAM chips lying around...stick them in to increase your memory.

---

### Post by rolandrock on 2011-02-28
[This is a good place to look]("https://help.ubuntu.com/community/SoundTroubleshooting")

---

### Post by beast2k on 2011-03-09
I can't be of much help to you, but I have the same sound card and mine does the same thing. I find if I wait about 30 seconds or so the sound smooths out and stops the skipping and cracking somewhat. I have tried all the fixes I could find and no luck here. If you happen to find a solution mark this thread solved, Ill keep an eye out, one thing is for sure we can't be the only 2 people with this trouble. :confused:

---


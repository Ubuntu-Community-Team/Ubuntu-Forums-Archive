---
title: "no sound AC97 Ubuntu 11.04"
date: 2011-08-29
forum: General Help
---

### Post by dlusseau on 2011-08-29
H folks,

I have a little sound problem with a clean install of Ubuntu Natty. 
1. old laptop that used to run XP, speakers/headphones worked before the install (not an output hardware problem)

2.clean install of latest version of Ubuntu (11.04)

3. I have no sound (no sound during booting, no sound effects, no sound playback (neither speakers, nor headphones)

4. checked all sound levels using alsa-mixer, sound prefenreces and pulseaudio controller. Nothing is muted

5. went through the various troubleshoots offered steps by steps (btw, those are really well written!). the laptop has an integrated soundcard (Realtek AC97 (rev 02) AD1981B) tried the different fixes for ac97_quirk adding them as options in the alsa-base (all details of setup at [http://www.alsa-project.org/db/?f=31dfa30679bbc8bd6cde646c4f8574b5d4bdcabb](http://www.alsa-project.org/db/?f=31dfa30679bbc8bd6cde646c4f8574b5d4bdcabb)). but nothing worked

6. what is very odd is that when I playback a sound I can see the sound volume moving in relation to the sound I should be earing in the PulseAdio volume control (!)

I am at a loss. Anybody has any idea?

thanks,
David

---

### Post by Horadranin on 2011-08-29
Can you hear anything using headphones?

---

### Post by dlusseau on 2011-08-29
no, no sound through headphones. I also tried reinstalling Ubuntu twice and that made no difference.

---

### Post by dlusseau on 2011-08-30
giving up on Ubuntu, reverting to XP. after 3 nights spent on this still no sounds and the OS does not handle well my old Nvidia card, graphics animations are very poor (eg google earth).

---

### Post by 3xp10r3r|X13 on 2011-08-30
I'm sorry to hear that... But could it be, that your laptop has several sound cards and the output is just set to the wrong one?
If it really is an old laptop I doubt it...but I felt like mentioning this.

-> there are lots of linux distributions out there, so don't go back to windows, just because ubuntu isn't working.

Fedora has a great hardware support. It is running gnome three by default and is supported by it's community + it doesn't limit you (as most linux distributions don't set boundaries) in any way .

I just like it a lot, so try it out

---

### Post by dlusseau on 2011-08-30
thanks. indeed only 1 integrated sound card. tried to get on with Fedora as well and similar issues. I think the hardware is too old (8 years) for the new distro. good old XP it is then.

---

### Post by gowings83 on 2011-09-01
I'm having the same problem.  It worked fine with Zorin (whoa never going back there).  Now I set up the system to dual boot with a barebones XP to only use for Netflix, the sound in XP is fine, but the Ubuntu doesn't work.  Judging by what I've read in here, looks like I'm putting my Soundblaster card in tomorrow.  Didn't need it before but guess I do now.

---


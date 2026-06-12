---
title: "So, Pulseaudio Is No Longer The Default in Kubuntu?"
date: 2009-08-10
forum: General Help
---

### Post by jlacroix on 2009-08-10
I thought it was wierd that when I was diagnosing an audio issue on my box, I did "sudo apt-get install pulseaudio" and it installed. I thought that was strange because I was under the impression that was already supposed to be there. I booted up a livecd, and sure enough, pulseaudio wasn't installed by default there either. Am I missing something, or is pulseaudio no longer the default for Kubuntu?

---

### Post by Screwdriver0815 on 2009-08-11
as far as I understood, Kubuntu uses X-Phonon. I also do not have pulseaudio installed, which is good because this way I do not have any sound trouble :guitar: :D

---

### Post by Barafu Albino Cheetah on 2009-08-11
I never saw pulseaudio configured in kubuntu by default. 
The truth about pulseaudio is "if you don't know why you need it - you don't need it". It can provide many desktop features such as lowering down sound when your phone calls or replacing film soundtrack with your favourite music, but none are implemented yet. Current use of pulse audio is for old or ported apps (not wine) and for high-end sound systems. 
Use alsa. link your phonon to alsa  too.

---

### Post by ilna on 2009-08-11
> **Barafu Albino Cheetah said:**
> Use alsa. link your phonon to alsa  too.How to?

---

### Post by Screwdriver0815 on 2009-08-11
> **ilna said:**
> How to?

its the default in Kubuntu.

But anyway, if you want to check it:

go to system settings --> Multimedia and check in all audio preferences if there is written in a point tip "this will try the following devices and use the first that works" and after that a list which contains "ALSA X-PHONON" when you point on your sound card.

---

### Post by ilna on 2009-08-11
> **Screwdriver0815 said:**
> its the default in Kubuntu.

But anyway, if you want to check it:

go to system settings --> Multimedia and check in all audio preferences if there is written in a point tip "this will try the following devices and use the first that works" and after that a list which contains "ALSA X-PHONON" when you point on your sound card.Unfortunately Phonon is stupid enough to fail in finding my card (RME/hdsp):

[http://ubuntuforums.org/showthread.php?t=1237215](http://ubuntuforums.org/showthread.php?t=1237215)

Probably it is "just upstream current state", so I'm in doubt wrt reporting new (k)ubuntu bug.

---

### Post by jlacroix on 2009-08-11
Thank you guys. 

My only outstanding problem is that the sound server is getting "stolen". What I mean is that if I run Amarok, Firefox won't play sounds. If I play something in Firefox, Amarok won't be able to. This is very strange to me because this laptop (Dell 15n) came with Ubuntu preinstalled so I though they would have chosen better hardware? Or is that not a hardware problem?

---


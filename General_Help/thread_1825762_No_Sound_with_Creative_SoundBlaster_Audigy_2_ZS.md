---
title: "No Sound with Creative SoundBlaster Audigy 2 ZS"
date: 2011-08-15
forum: General Help
---

### Post by Haneef Mubarak on 2011-08-15
I am unable to get the sound to work on my Dell Dimension 4600. 

Recently, I bought a new hard drive and installed Ubuntu Server 11.04 (natty) on it. Then I set up something so that if I needed the GUI (Xorg with GNOME) I could access it (while already logged into the shell) by typing "startx". This worked pretty well, but when I attempted to test the sound, I couldn't hear anything. 

I have already tried the *[** **]("http://ubuntuforums.org/showthread.php?t=205449")[Comprehensive [I]Sound* Problem Solutions Guide]("http://ubuntuforums.org/showthread.php?t=205449"), [/I][*Debugging [I]Sound* Problems - *Ubuntu* Wiki[/I]]("https://wiki.ubuntu.com/DebuggingSoundProblems")*, *and [*SoundTroubleshooting - Community [I]Ubuntu* Documentation[/I]]("https://help.ubuntu.com/community/SoundTroubleshooting")*, *but all with no avail.

I do also have an [*ALSA info script* for my issue]("http://www.alsa-project.org/db/?f=53a63ff8f829502f58e440172fe6971cf610b7e9").

---

### Post by Haneef Mubarak on 2011-08-16
Help?

---

### Post by merlin371 on 2011-08-16
download gnome-alsamixer package then go into it, and tick the "audigy analog/digital output jack"

---

### Post by Elfy on 2011-08-16
No idea if it's the case with this card but my old audigy always starts with the digital/analog switch on - try toggling that. 

You might need to add the switch channel to the sound preferences to see it.

If you've done other things trying to get it to start you possibly might have to backtrack.

---

### Post by Haneef Mubarak on 2011-08-16
Neither worked. I did try toggling the Analog/Digital Jack option, but it still won't work. And my gnome-alsamixer looks different (btw, it only launches via gksu).

---

### Post by Haneef Mubarak on 2011-08-18
Bump...

---

### Post by Haneef Mubarak on 2011-08-19
I hate to have to bump, but...

BUMP!

---


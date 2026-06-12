---
title: "Please community help me configure &quot;Front Panel&quot;"
date: 2011-04-14
forum: General Help
---

### Post by Julian Luna on 2011-04-14
Hello people well there's a panel in the front wich manages 2 usb spots  (That work fine) And input and an output, i'm using ALSA on ubuntu 10.10  and if I plug my earphones on the front (Which is actually what  interests me...) I can't get to hear anything :sad:  Proper work would be to... instantly when I plug them, speakers shutup  and I hear stuff on the earphones right? My motherboard is made by  EliteGroup, A780GM-A model and it's black series. I really need to get  it to work cause I need to produce some music and it's stressing for the  people around to hear the same sounds over and over during the build of  a new song. Ty :]

---

### Post by Krytarik on 2011-04-15
How about the settings in "System -> Preferences -> Sound -> Output"?

You can also install the package "pavucontrol" to get more control over your sound settings, you will find it in "Applications -> Sound & Video -> PulseAudio Volume Control" after the installation.

Hope it helps!

---

### Post by Julian Luna on 2011-04-16
Well everytime I try to open the Sound Preferences there's a message "Waiting for sound system to respond" that stands there forever... I have googled and read something about deleting the ".pulse" folder that's into my home folder but everytime I delete it; it keeps "Recreating" Itself... it just shows up over and over! ... it's like ******* Cell at Dragonball... really freaking me out... people says it's a definitive solution since i'm using alsa and not pulseaudio, but I wish there's another way to make my Sound Preferences load taking in mind Alsa... Atm i'm installing pavucontrol but i've already read on it's description it's pulseaudio's software, don't know if it's gonna work for me since i'm using Alsa. (Needed to move from Pulse to Alsa because pulse wasn't able to mix different sounds at one time, just one sound at time. It's already installed, tried to run it and it does not work. "Connection failed: Connection refused". I'm pretty sure it haves to do with the fact i'm using alsa but... any other solution ppl? D:

---

### Post by Krytarik on 2011-04-16
I, too, did some googling just yet, and I saw some threads, including the one you did, where everyone says that removing those directory fixed the issue. I'm not really a sound expert, and I don't know how to fix the issue that led you to purge pulseaudio, but since you did so, of course pavucontrol can't do anything, and it seems that "Sound" preferences also relies on pulseaudio.

---


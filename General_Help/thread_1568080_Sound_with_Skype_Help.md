---
title: "Sound with Skype Help?"
date: 2010-09-04
forum: General Help
---

### Post by ineedhelp123 on 2010-09-04
alright so I cant get the sound for my skype to work and I have read some other forums about that but can anybody give me step by step help on how to fix this? i know it has to with the ALSA and OSS. and i have tried to fix it through pulse audio management but it just isant working help meeeeeeeeee!!!!!

---

### Post by dirghrabadia on 2010-09-04
What Skype version do you have? I had problems with audio on Jaunty, but since I upgraded to Lucid, its working great.

---

### Post by Jazzy_Jeff on 2010-09-04
Are you using Ubuntu 10.04? Do you get any sound from Skype at all or are you having problems with the mic part of it?

---

### Post by ineedhelp123 on 2010-09-04
I have skype version 2.1 Beta and yes i am using Ubuntu 10.04 and the only part of skype that doesnt work is the mic. my friends cant hear me but i can hear them and there is nothing wrong with their speakers

---

### Post by Jazzy_Jeff on 2010-09-04
Open up a terminal and type in alsamixer. Use the arrow keys to move the cursor over to the right and look for mic. It will probably give you a couple of choices. Make sure the volume level is up on them and also the mic gain. At the bottom of the bar it should say OO. If it says MM just hit the m key on the keyboard to change it. See if this works for you. 

If not then goto the sound applet on your bar and go to preferences and click on input. Toggle between the choices while talking into mic until you see the volume level move. For some reason when I restart my computer I have to go into this and move it from one to the other and back again to make it work. 

Let me know if this works for you.

---

### Post by ineedhelp123 on 2010-09-04
Is a terminal when you press alt then F2? Sorry still new to Linux.

---

### Post by beren.olvar on 2010-09-04
what's your sound card?
is your microphone working with other applications?
Are you sure you have selected the right source in skype->options->sound devices ?

also maybe posting the output of "pacmd list-sources" would give some information.

---

### Post by jeight on 2010-09-04
Applications - Accessores - Terminal

---

### Post by Jazzy_Jeff on 2010-09-04
> **ineedhelp123 said:**
> Is a terminal when you press alt then F2? Sorry still new to Linux.

Go to Applications>Accessories>Terminal

---

### Post by dirghrabadia on 2010-09-04
Under Options in Skype 2.1 Beta, I have everything set to PulseAudio Server (local), for microphone, speakers, and ringing sound devices.

---

### Post by ineedhelp123 on 2010-09-04
my mic was on according to the terminal and beren.olivar i dont even know how to get to my sound card. and the only time my mic will work is if i plug in a mic and i can hear myself but barely. is there any way i can get the built in mic on my cpu to work?

---

### Post by ineedhelp123 on 2010-09-04
I have everything under pulse audio too its just not working for some reason.

---


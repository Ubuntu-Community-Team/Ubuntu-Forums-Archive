---
title: "Problems with sound in Lucid 10.04"
date: 2010-05-09
forum: General Help
---

### Post by DeMus on 2010-05-09
Hi,

When Lucid was released I installed it immediately, which was something I better had not done: I had a lot of problems with the new O.S.
Just when I was finished with Ubuntu I found Ubuntu-Studio and decided to install that. It worked as it should, except for the sound. I can boot the computer and have sound where I want it. Then suddenly, and don't ask me what happens in the mean time, the sound is gone: Banshee doesn't play songs anymore and shuts down after 5 times trying to play a song, system sounds don't work anymore, flash has no sound, nothing.
I used Studio for a while but today I though let's go back to Ubuntu Lucid. This time not the 64 bit version but the old-fashion 32 bits.
First I thought WOW, it really works, everything works, but then just now sound stopped again. Completely.
Banshee crashes again when trying to play a song, Flash is quiet, just the sounds in Google-Chrome still function.

When you want to know which sound-system I use, I did a normal installation without any changes to sound whatsoever. Is that alsa, is that pulse-audio, I have no idea.

What can cause this behavior and what can I do about it to stop it?

---

### Post by dino99 on 2010-05-09
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

you might have some more info if you look at .xseesion-errors and logs

dont forget to install: paprefs, gnome-alsamixer (tweak it), ubuntu-restricted-extras, and medibuntu repo for codecs. If compiz is installed it could cause your issues

---

### Post by DeMus on 2010-05-09
After experimenting some more it seems that the sound system can handle only 1 stream at a time. Also, once I have used sound all others can not be used anymore. Message: system is in use.
How can I change this? It must be possible to handle more than one sound at a time, isn't it?

---

### Post by dino99 on 2010-05-09
its ok search and look at pulseaudio doc for mixing sounds, but usually users dont want that  :confused: (settings are into system.pa or default.pa dont remember.

if pulseaudio is still running in the background, kill it :P

then sudo dpkg-reconfigure pulseaudio

might need to remove .pulse for better result

---

### Post by DeMus on 2010-05-09
> **dino99 said:**
> its ok search and look at pulseaudio doc for mixing sounds, but usually users dont want that  :confused: (settings are into system.pa or default.pa dont remember.

if pulseaudio is still running in the background, kill it :P

then sudo dpkg-reconfigure pulseaudio

might need to remove .pulse for better result

Thank you for your help but how do I kill pulseaudio processes? They keep coming back with  another process number.

---

### Post by lancerocke on 2010-05-10
> **DeMus said:**
> Thank you for your help but how do I kill pulseaudio processes? They keep coming back with  another process number.
bump

---

### Post by DeMus on 2010-05-10
Things are different every time I boot. Now I have a situation that when I started Google-Chrome I had sound, then when I switched from one TAB to another no more sound. I started Banshee and it won't play my songs at all: Banshee just crashes completely. Now I am importing songs in Rhythmbox and I get the following message when starting to play a song:
```
Failed to open output device: Failed to connect stream: Too large
```
What does that mean and how can I solve it? Slowly I am getting completely crazy from Ubuntu 10.04. I'm really thinking about going back to Jaunty, that just worked for me.

Edit:
I believe, although it might be too early to tell, I found it. I had the sounds add-on installed in Google-Chrome and whenever I started Chrome the problems started. So, now I am using Firefox for a while to see if I am right. I have un-installed the sounds add-on but still will use Firefox. Now I hope the sound problems are definitely gone. They were really annoying me.

---

### Post by dianne2208 on 2010-05-22
Try doing what Felix Kronn said in post #16 of this bug in launchpad, 
[B][Bug #362423 in totem  (Ubuntu): “"*Failed to connect stream*: *Too large*"”]("https://bugs.launchpad.net/ubuntu/+source/totem/+bug/362423")
[/B]```
pulseaudio --kill
```
```
pulseaudio --start
```Those two commands are what fixed mine, I hope they will help you too. Good luck!

---


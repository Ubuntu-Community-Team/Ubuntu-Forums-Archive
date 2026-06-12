---
title: "help AC97 audio controller!!!"
date: 2009-06-28
forum: General Help
---

### Post by Benzaa on 2009-06-28
Does anyone know how to activate the microphone for this audio card??

I've trying a lot of things but nothing is working.

Please, help, I want to use skype with Ubuntu

---

### Post by credobyte on 2009-06-28
What devices you've set in your Skype settings ( default, pulse, alsa .. ) ?

---

### Post by Benzaa on 2009-06-28
I've used alsa.

But I cannot even record. I have tried changing to all the options; OSS, pulseaudio, alsa.

---

### Post by credobyte on 2009-06-28
Don't use Alsa ( at least it does not work for me ) - use pulse ! If it still does not work, sorry, can't help you ..

---

### Post by Benzaa on 2009-06-28
do you have the same sound card??

00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)

---

### Post by credobyte on 2009-06-28
> **Benzaa said:**
> do you have the same sound card??

00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)

AC'97, tough, not from Intel :
```
nForce3 250Gb AC'97 Audio Controller
```

---

### Post by maxpathan on 2009-06-28
Hi
I had the exact same problem. Trying to use skype.

I went to the OPTIONS > SETTINGS

for SOUND IN select  SiS S17012

That worked for me :-)

---

### Post by Benzaa on 2009-06-30
> **maxpathan said:**
> Hi
I had the exact same problem. Trying to use skype.

I went to the OPTIONS > SETTINGS

for SOUND IN select  SiS S17012

That worked for me :-)

Where did you select that option??
I dont have SiS S17012??

Where you able to record after changing that??

---

### Post by maxpathan on 2009-07-29
> **Benzaa said:**
> Where did you select that option??
I dont have SiS S17012??

Where you able to record after changing that??

It was just one of the options available. Sorry I cant be of more help.

---

### Post by apparle on 2009-07-29
My AC'97 audio controller mic was muted by default
Check if you have selected the audio input device correctly in the settings(I don't remember exactly where are these, as I use Kubuntu).
Also try alsamixer command in terminal and check if the mic is selected or not.
Also I tried OSS drivers. They also don't have the correct mic input selected.
If you install OSS then select the channel with the help of the GUI mixer of OSS system.
The command is something like ossxmix or something like that

---


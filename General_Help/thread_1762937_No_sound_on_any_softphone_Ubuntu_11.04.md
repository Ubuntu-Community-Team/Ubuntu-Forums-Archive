---
title: "No sound on any softphone Ubuntu 11.04"
date: 2011-05-19
forum: General Help
---

### Post by romulusro on 2011-05-19
Hi, Could someone give me an idea how I can fix this problem ?
I have installed linphone, ekiga, twinkle and with all off them I can make calls but I don't hear any sound. 
Playing music, audio system works well without problems

I have change the sound parameters, installed alsa-oss package, played with mixers, searched on the forums but with no luck.

Thanks in advance for your help

---

### Post by crashed111 on 2011-05-19
Have you checked your mic is not muted (Click on the speaker at the top of your screen and go into to sound preferences then look at the input tab. There is an input volume which is set there)

---

### Post by romulusro on 2011-05-20
there is not a problem in mic, it is on and it is working well.
When I make a call I don't hear nothing, no ring tone, and neither when call is started I don't hear the other person.
Any suggestions please ?

---

### Post by romulusro on 2011-05-20
any idea ?

on skype both the speakers and the microphone work well, but on any softphone they are not

---

### Post by Ashtonford on 2011-05-28
> **romulusro said:**
> any idea ?

on skype both the speakers and the microphone work well, but on any softphone they are not

I have been going thru the same problem! none of the soft phones work on ubuntu 11.04 and it dosent seem to be anyone getting the no sound problem fixed!

---

### Post by linuxinstalledfromhdd on 2011-05-28
Just out of curiosity, did you guys try 10.10?

---

### Post by romulusro on 2011-05-29
yes, but I didn't use any softphone on ubuntu at that time
now, I have installed on another partition windows just so I can use this kind of applications

---

### Post by gandaran on 2011-05-29
> **romulusro said:**
> there is not a problem in mic, it is on and it is working well.
When I make a call I don't hear nothing, no ring tone, and neither when call is started I don't hear the other person.
Any suggestions please ?
I also have a microphone sound problem with linphone, I can hear the ring tone and the person speaking on the other side but they cant hear me! I also tried ekiga on natty but ditched it because it was complaining about firewall port forwarding when ekiga used to work very well on ubuntu 10.10, my mic sound problems started when I bought a new motherboard with HDA Intel IDT 92HD73C1X5 sound card, the mic only works on the front jack with the sound recorder.

---

### Post by digital9ja on 2011-07-12
I was screwing around trying to get twinkle working for awhile tonight on xubuntu 11.04. I made sure my mic was unmuted on my inline headset selector first, then checked to be sure it wasn't muted anywhere in twinkle, in alsamixer, in pulseaudio (I installed the paman package to manage it and then started it from multimedia). Nothing was working. Finally I noticed the setting in alsamixer called mono out. It was set to mix. I changed that to mic and voila! Everything seems okay now, I made a test call to a co-worker and it was all good.

Hope this helps someone else, I know what a PITA it can be to try and get this kind of thing to work sometimes. I hate how there are so many different places where a simple mute button can be toggled on and until you find it you're SOL. Good luck to anyone working on a similar issue, hope you get it figured out soon. Sure is a relief.

---


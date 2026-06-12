---
title: "Soundblaster Audigy - no surround (5.1) sound"
date: 2006-04-21
forum: General Help
---

### Post by pivoto on 2006-04-21
I am running on Ubunto Breezy. Alsa 1.09 is installed, I have sound but only on the 2 front speakers. The ALSA mixer shows other speakers but they are silent.

What can be the problem and how can I fix it ?:confused:

---

### Post by RobMongoose on 2006-05-06
Has anyone found a fix for this? I'm having the same problem - Running on a fully up-to-date Kubuntu Breezy, with a Soundblaster Audigy SE - sound is coming from the front speakers, the other speakers are showing in alsamix, but no surround sound. The speakers aren't muted, and moving the sliders does nothing.

I've upgraded alsa to 1.0.11 as shown [here]("https://wiki.ubuntu.com/HowToConfigureSoundBlasterAudigySEinBreezy") in the Ubuntu wiki, but still no surround sound.

Please can some one help with this, it's driving me nuts! ](*,)

---

### Post by Haegin on 2006-05-06
Make sure the Audigy Analog/Digital Output Jack is NOT muted· This is a common problem with the audigy cards I think·

---

### Post by RobMongoose on 2006-05-06
here's my alsamixer settings - 

[IMG]http://www.robmongoose.plus.com/images/alsamixer.png[/IMG]

If I activate the SPCIFout I get no sound at all, and everything else is turned up.

Can anyone see anything wrong here? Is there any more info I can post that would be helpful?

Thanks :)

---

### Post by Haegin on 2006-05-07
Try lsmod and make sure the module required by your card is being loaded and that you are not using a driver that only just works for your card. [http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Creative_Labs#matrix](http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Creative_Labs#matrix)

Also I know this is prob an insult to your intelligence but check all the connections...

---

### Post by RobMongoose on 2006-05-07
Thanks for the suggestion :) 

I've tried what you said and running lsmod shows that the snd_ca0106 module is being loaded and the alsa site says CA0106 is the right module for my card so that seems to be ok.

And no offense taken on the connection suggestion :) it happens to the best of us, but the surround sound works fine if I boot to windows, so it must be connected ok.

Any other ideas?

Thanks

---

### Post by RobMongoose on 2006-05-09
*bump

:P

---

### Post by shurguywutt on 2006-05-14
I have a SB Live 24 bit card and it is a real pain in the butt, alsa really hates soundblaster I guess.  Sometimes I have sound, other times I don't... Soundblaster really needs some decent linux drivers.

---

### Post by Citizen Kane on 2006-05-15
Same here. On win a good card, on linux a pain in the posterior. My build-in Via card works nice, but the CA0106 soundblaster live 24 bit doesn't wanna work. Mayhaps this has something to do with having an on-board soundcard at the same time. anybody know a workaround for this?

---

### Post by RobMongoose on 2006-05-15
I disabled mine in my BIOS - maybe your motherboard has the same function. Hasn't fixed the problem though :(

I just don't get it... Kmix and alsamixer can both see that there are other sound channels there, they just won't pipe any sound through them. Seriously irritating.

---

### Post by Luke Davis on 2007-04-25
I have a sound Blaster Audigy SE (Module CA0106) as well. The surround sound doesn't work. Just the front two seapkers. 
Just like everyone else it appears. I have tried the alsamixer volume controls; all the posible options. Still no luck.
It works fine in Windows (not that I even have it installed anymore) 
I have used my amplifier controls to emulate the sound but it is just copying the front speakers output to the rear and that is not a real solution. Any ideas about how to fix this, short of getting a compatible sound card would be appreciated

---

### Post by RobMongoose on 2007-04-26
Hi,

I posted the fix that worked for me on [this thread here]("http://ubuntuforums.org/showthread.php?t=184814")

Hope it helps

---


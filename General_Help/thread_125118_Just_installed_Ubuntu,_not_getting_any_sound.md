---
title: "Just installed Ubuntu, not getting any sound"
date: 2006-02-03
forum: General Help
---

### Post by wootlands on 2006-02-03
i did a search for "blank cd player" and didn't see any results that sounded like my problem.

i'm new to linux, just installed ubuntu 2 days ago, and just now tried to go to a site that has a flash animation with sound. the sound didn't come out, so i plopped in a cd, and the cd player said "blank cd". i shut down the cd player, restarted it, and it picked up the CD just fine, but still no sound is coming out. I fiddled with the volume control and made sure everything was turned up, but honestly, there's about 100 options under Preferences when I select my Sound Blaster Audigy 2 ZS. Some are doubled up, but there's 98 EMU10K1 PCM * options (so, maybe there's 200+ items that can be checked). It's nearly 1am, I'm braindead and totally new to this OS. what might the problem be?

thanks in advance.

---

### Post by _simon_ on 2006-02-03
I've got the same card. All I did was turn on the Audigy settings in alsa mixer. At work at the moment so can't check but I think there's 3 of them.

---

### Post by wootlands on 2006-02-03
when you get home, can you check? :D 

it's driving me nuts...

---

### Post by TechSonic on 2006-02-03
There can be many reasons why you don't have sound.  First, what kind of Sound Card are you running?  Brand Name + Version and I can start helping you out.  Audigy isn't discriptive enough.

Current Sound Blaster Compatible cards.
Sound Blaster Audigy 1 (Half Duplex) - ALSA Only
Sound Blaster Audigy LS (Half Duplex) - ALSA Only
Sound Blaster LIVE! 24 bit (Half Duplex) - ALSA Only
Sound Blaster Audigy 2 (Half Duplex) - ALSA Only
Sound Blaster LIVE! 5.1 or 5.1 Digital (Full Duplex) - ALSA & OSS With ESD Combo.

---

### Post by wootlands on 2006-02-07
Sound Blaster Audigy 2 ZS is the sound card (as stated above). beyond that, I'm not sure what you would want in response to brand name + version... :confused:

---

### Post by suhara on 2006-04-15
Please somebody help me...

I just installed my Ubuntu 5.1 on my PC
specs:
AMD 64 3500+
ECS K8T890-A
Sound blaster live 5.1
NVIDIA GFORCE 6600 PCI-e

Why I couldn't enter ubuntu
on the logging ubuntu desktop the sound loop ..
beep beep beep beep
and after I enter the user name and the password
it's hangs 

please help me, I will very appreciate for some hands

---

### Post by graigsmith on 2006-04-16
well i checked alsa's website and it looks like your card is supported, as long as its not the usb video input one.  

heres that webpage to check the support of your card. 
[http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Creative_Labs#matrix](http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Creative_Labs#matrix)

if its supported then it should work flawlessly.. go into alsa mixer. 
open a command prompt, and type alsamixer
hit f5, and turn the volume up on everything with the cursor keys.  if somethings muted it will have MM on it, hit m key to unmute it.  then your sound should hopefully work.

---

### Post by dragge on 2006-04-16
[QUOTE=wootlands]i did a search for "blank cd player" and didn't see any results that sounded like my problem.

i'm new to linux, just installed ubuntu 2 days ago, and just now tried to go to a site that has a flash animation with sound. the sound didn't come out, so i plopped in a cd, and the cd player said "blank cd". i shut down the cd player, restarted it, and it picked up the CD just fine, but still no sound is coming out. I fiddled with the volume control and made sure everything was turned up, but honestly, there's about 100 options under Preferences when I select my Sound Blaster Audigy 2 ZS. Some are doubled up, but there's 98 EMU10K1 PCM * options (so, maybe there's 200+ items that can be checked). It's nearly 1am, I'm braindead and totally new to this OS. what might the problem be?

thanks in advance.[/QUOTE]

If you are using the Audigy Analog/Digital Output Jack, if you are using some sort of surround sound, make sure u have unmuted the Analog/Digital Jack in alsamixer. By default its muted. When i first installed Ubuntu i had no sound either and took me 2 hours before i found that out, that it's muted by default :D

---


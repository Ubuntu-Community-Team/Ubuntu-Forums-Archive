---
title: "ubuntu 10.04 pulseaudio sound problem"
date: 2010-04-28
forum: General Help
---

### Post by spayman on 2010-04-28
[B]Hello everyone :)
well , my bad english won't let me describe my problem :(
any way , i have ubuntu 10.04 lucid lynx , everything running well
and really like it =)
the only problem i got is that the sound doesn't work :(
well , it works , but .... mhmm !
when i try to call someone on skype or i try to record my desktop on a video(gtk-RMD)or open a media program (like sounds editors and ... ) the sound disepears , and the sound icon on the top panel , gets grey (disactived or something) 
( sorry for my bad english )
please help me :( that's really really botherin me :(
and ths are the results of (pulseaudio command)[/B]
> kyle@ubuntu:~$ pulseaudio
E: pid.c: Daemon already running.
E: main.c: Échec de pa_pid_file_create().
**sorry for my bad english again , help me please :(**

---

### Post by spayman on 2010-04-28
come on please :(
i'll give you beans :KS

---

### Post by spayman on 2010-04-28
no one =( ?
please , am begin ? :(
please damn , please
please !

---

### Post by Sin@Sin-Sacrifice on 2010-04-28
Is skype set to use pulseaudio? Check skype's preferences for sound.

---

### Post by spayman on 2010-04-28
I tried , when i try to call , skype freezes :(
thanks for answering any way :(

---

### Post by Sin@Sin-Sacrifice on 2010-04-28
I did a little research but don't use skype so I can't test it. It seems there's been a few workarounds interred that I found googling. I came across one post that said to set audio in skype to ALSA because the devs set skype to use the pulse_pcm driver for ALSA. Hope this helps.

---

### Post by spayman on 2010-04-28
mhmm :)
how to change this thing :S
thanks for searchin , and helping a weak poor noob :)

---

### Post by spayman on 2010-04-28
woot , i found it :) and yes it's on pulseaudio 
but when i try to change it , it doesn't
there is only pulseaudio as option :S
no alsa nothing :(

---

### Post by dino99 on 2010-04-28
install gnome-alsamixer and paprefs if not yet, then set volumes into gnome-alsamixer

---

### Post by spayman on 2010-04-28
whoa :D
yo dude , thanks , it's working =)
thank you very much , i really appreciate ur help :)
thank you !

---

### Post by sosias on 2010-05-01
didn't work for me :confused:

---

### Post by whit on 2010-08-23
Not for me either. Is there some way to rip pulse out of the system and run something that doesn't fail so many people so often?

---

### Post by Azyx on 2010-09-07
> **dino99 said:**
> install gnome-alsamixer and paprefs if not yet, then set volumes into gnome-alsamixer

Thanx :) gnome-alsa-mixer work just fine :) alsamixergui, did not work (only showed master and caputure) and say that my card and chip was pulseaudio....With gnome-ALSA mixer I se all my controlles for 7.1 surround and controlls for my TV-tuner-card :)

---


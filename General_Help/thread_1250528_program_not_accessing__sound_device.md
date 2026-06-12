---
title: "program not accessing  sound device"
date: 2009-08-26
forum: General Help
---

### Post by rhythmiccycle on 2009-08-26
I have a problem with Gtick.

off of a fresh reboot, it runs fine.

but after i run other programs, and then try to use Gtick again, i get the message:
> 
Couldn't start metronome.
Please check if specified sound device
and sample file are accessible.


when i reboot i can run the program, but i would prefer not to have to reboot every time i run the program.

is there a way to reboot the sound device, without rebooting the whole system?

---

### Post by BslBryan on 2009-08-26
Do you use pulseaudio?  There's a bug in some computers that don't allow more than one application to use the sound card.  

Have you tried running it without anything else open?  

Anyway, assuming that you do use pulseaudio, the following commands should work.
```
sudo killall pulseaudio
pulseaudio
```

---

### Post by rhythmiccycle on 2009-08-27
that code did the trick. 

thanks BslBryan!!

---


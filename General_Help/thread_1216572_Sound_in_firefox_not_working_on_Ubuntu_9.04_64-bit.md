---
title: "Sound in firefox not working on Ubuntu 9.04 64-bit"
date: 2009-07-18
forum: General Help
---

### Post by beattyml1 on 2009-07-18
My sound won't work in firefox on the latest install

[LIST]
[*]Firefox 3.0
[*]Ubuntu 9.04
[*]64 bit
[*]Sound does work in flashplugin when used in moovida media center but not in firefox also other sound beside flash did not work in firefox
[/LIST]


I have sound working on
[LIST]
[*]Old Ubuntu 9.04 64-bit upgraded 8.10
[*]Fresh Install of Ubuntu 9.04 32-bit
[/LIST]

Any Ideas?

---

### Post by beattyml1 on 2009-07-24
Anyone?

---

### Post by beattyml1 on 2009-08-02
I just tried a new 32 bit install and I got the same problem, although I thought on my last 32 bit install I didn't run into this problem, the only thing that I can specifically think of that I did different is that this time I copied my home folder from the old 64-bit install to the new 32-bit install.

---

### Post by beattyml1 on 2009-08-02
Also in pulse audio mixer I just noticed that it shows firefox as alsa plugin[firefox]

---

### Post by beattyml1 on 2009-08-14
Alright so I now know what the problem is but need some help fixing it:

The problem is that firefox is routing it's sound straight to a specific alsa output (or at least I believe thats what it is) but it is not my main sound output.   I have to sound cards, one that I use for recording, the other for home user type audio.  Firefox is on the recording card, I want firefox on the home user type audio card.  Any ideas?

---

### Post by pjcdawkins on 2009-09-11
This is just to say I have the same problem.

---

### Post by mehaga on 2009-09-11
I had the same problem and the way i fixed it was ridiculous. Start mixer and unmute/increase PCM channel volume :)

---

### Post by misfitpierce on 2009-09-11
Try hitting System-Preferences-Sound

Change from autodetect to another one that works by hitting test. Change them up then restart to give it a full test and see if it works... If not try another one that you can hear beep on... save and restart and check again... Check to see if that process works for you... Remember if you can't hear a beeping noise when you hit test then don't use that one as its not putting out sound. This worked on friends computer.

---

### Post by fougas on 2009-09-16
> **vekaz said:**
> I had the same problem and the way i fixed it was ridiculous. Start mixer and unmute/increase PCM channel volume :)

lol same here! :)

---


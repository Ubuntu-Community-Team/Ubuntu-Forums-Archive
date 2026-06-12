---
title: "sound quality"
date: 2006-06-26
forum: General Help
---

### Post by tipi on 2006-06-26
Hi there,
just a question,
I have win32 codecs and so installed, and have tried using various mediaplayers
beep, xmms ... and am using a little sound system with subwoofer.
when I play the same mp3 under windows with winamp the sound quality is alot better
than under ubuntu.
would like to use Ubuntu more, can I do something about this
greetz

---

### Post by woedend on 2006-06-26
use alsamixer to adjust the bass/treble(tone must be turned on).
also, turn the value "front" down to 74 or so if you are getting static at full volume.

---

### Post by matrooswolf on 2006-06-26
open volume control (Alsa mixer) and slide the PCM slider down to about 70 %, above that sounds degrades

---

### Post by woedend on 2006-06-26
@matroos -
If the option for "Front" is available, I find it much easier to use that.
It seems to do the same thing as PCM, but the problem is that some applications use PCM volume.  So if you crank it up, you are cranking PCM up.  Front value never seems to change.  By default Dapper comes with 80%, i've found 74 is the most it should be.  This allows you to crank PCM to 100% with no ill effects.
I don't know if its just with Sound Blasters or all cards, but this option seems a little more sane as PCM is rather dynamic.

---

### Post by joshrobinson on 2006-06-26
[QUOTE=woedend]@matroos -
If the option for "Front" is available, I find it much easier to use that.
It seems to do the same thing as PCM, but the problem is that some applications use PCM volume.  So if you crank it up, you are cranking PCM up.  Front value never seems to change.  By default Dapper comes with 80%, i've found 74 is the most it should be.  This allows you to crank PCM to 100% with no ill effects.
I don't know if its just with Sound Blasters or all cards, but this option seems a little more sane as PCM is rather dynamic.[/QUOTE]

my laptop does the same thing off and on.. its a gstreamer issue as far as i can tell.. ive always turned the PCM down personally.. programs i use i tell to adjust master and not PCM, but i will try your way out too if i ever get a program that i can ttell to use master

---

### Post by matrooswolf on 2006-06-26
[QUOTE=woedend]@matroos -
If the option for "Front" is available, I find it much easier to use that.
It seems to do the same thing as PCM, but the problem is that some applications use PCM volume.  So if you crank it up, you are cranking PCM up.  Front value never seems to change.  By default Dapper comes with 80%, i've found 74 is the most it should be.  This allows you to crank PCM to 100% with no ill effects.
I don't know if its just with Sound Blasters or all cards, but this option seems a little more sane as PCM is rather dynamic.[/QUOTE]

Thanks, I didn't know that.  

I opened alsamixer, but I don't have front?  Is that correct?  Or am I missing something?

(I don't have a soundblaster, just sound on board SiS SI7012)

---

### Post by woedend on 2006-06-26
i was afraid of that...it must be sound blaster related.  Do you have any other sliders which may affect the volume?

---

### Post by v4169sgr on 2006-06-26
KMix will display different settings according to your auto-detected sound card(s). There's a useful integral help in the application.

Does anyone have a pointer for *strategies* in use for setting KMix settings for optimum use e.g. playback without static at higher volumes?

---


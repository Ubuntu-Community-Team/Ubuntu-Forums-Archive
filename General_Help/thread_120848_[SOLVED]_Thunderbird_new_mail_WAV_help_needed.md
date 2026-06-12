---
title: "[SOLVED] Thunderbird new mail WAV help needed"
date: 2006-01-23
forum: General Help
---

### Post by rfruth on 2006-01-23
I use Tbird 1.0.7 and all is well almost, when I try to use a "custom .wav file" for new mail all I get is a short burst of static (Totem can play the same WAV files no problem ) so my workaround is to use use the default new mail sound (a beep) anyone using custom .wav files with Thunderbird ?

---

### Post by bschuteker on 2006-01-24
I am using a custom wav. All I did was put the wav in my home dir and then on TB point to is and it works just fine  as long as no other program has sound locked out. It seems that if I'm playing music with Amarok (which I do A LOT) I get no other sounds.

Good Luck

---

### Post by queenorych on 2006-01-24
I had an old wav file that wouldn't work in evolution.  I ran it through sox creating the same quality wave file, and it worked just fine.

---

### Post by dr_paranoisky on 2006-01-24
same probleme here with tb 1.5.
can play my wav in mplayer. in thunderbird it sounds very bad. rrrrrrrrr.
any further ideas?
thX!

---

### Post by rfruth on 2006-01-24
Per the Mozilla/Thunderbird forum [http://forums.mozillazine.org/viewtopic.php?t=371756]("http://forums.mozillazine.org/viewtopic.php?t=371756")
Mac OS X had sound problems with ver 1.0.7 but were addressed in ver 1.5 - this is F Y I

---

### Post by zaziork on 2006-07-30
I had the same problem; it turned out that the WAV I was trying to play was actually encoded as an mpg.

I converted the mpg to wav using "mpg321" (easy to download and install with synaptic).

Then from the command line:

```
mpg321 -w NEWfile.wav OLDfile.wav
```

Hope this helps someone..!

---

### Post by peachy on 2006-10-18
> **zaziork said:**
> I had the same problem; it turned out that the WAV I was trying to play was actually encoded as an mpg.

I converted the mpg to wav using "mpg321" (easy to download and install with synaptic).

Then from the command line:

```
mpg321 -w NEWfile.wav OLDfile.wav
```

Hope this helps someone..!
This worked for me with Thunderbird 1.5.0.7, thank you knindly :D

---

### Post by phil90 on 2007-05-29
edited

---


---
title: "Minimal Music PC?"
date: 2011-05-26
forum: General Help
---

### Post by themarker0 on 2011-05-26
I have a couple of older P3 Pc's lying around with 20GB HDD's in them. Currently one has FreeBSD, the other Ubuntu server. (A mirror of my VPS) What i would like to do is dump all the data i have from my FreeBSD server, and to install Ubuntu Minimal on it. Then i think i'd like to have a music PC. Either to stream or to play. Is this possible without installing a UI? I personally would rather not, as not much else then openbox will run well. Has it been done before, as there any good applications? Any and all help is deeply appreicated.

---

### Post by Irihapeti on 2011-05-26
It's been a while since I did this, so others may be better informed than I am, but I did play briefly with something of this kind.

I used ogg123, mpg123 and aplay (alsa) to playback Ogg, Mp3 and wav files respectively.

The first two seem to have been replaced in Natty with music123

I think that gpac includes a mp4 streaming program, probably for movies.

If you want a kind of graphical interface in a terminal, there is mp3blaster.

I suggest searching in synaptic package manager and seeing what you can find. There are definitely some intriguing programs there!

---

### Post by themarker0 on 2011-05-31
Would you use the server or the minimal and compile (install) alsa?

---

### Post by WorMzy on 2011-05-31
I'd use arch. All you'd need to do is set up ALSA (or OSS), MPD, and MPC (or ncmpc).

Edit: here's a screenshot of ncmpc running in a virtual terminal, it's got a very intuitive interface.
[URL="http://img651.imageshack.us/img651/2007/84945633.png"]
[IMG]http://img651.imageshack.us/img651/2007/84945633.th.png[/IMG][/URL]

---

### Post by jamesisin on 2011-05-31
Do you intend for this machine to perform playback or merely file serve?

I'm running a great system here file serving to a hi-fi computer for playback.

I can control that hi-fi system from other computers on my network (either by a small script for Rhythmbox or by calling Rhythmbox across ssh using the remote x--making this craptastic netbook a semi-cool remote control).

Here is an article on my script:

[http://jamesisin.com/a_high-tech_blech/index.php/2010/11/script-for-skipping-tracks/](http://jamesisin.com/a_high-tech_blech/index.php/2010/11/script-for-skipping-tracks/)

I haven't written an article yet on running Rb over ssh, but if you want me to talk about that let me know.

---


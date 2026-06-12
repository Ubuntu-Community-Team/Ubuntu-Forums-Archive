---
title: "Internal microphone not working in 11.10"
date: 2011-12-11
forum: General Help
---

### Post by pretty_whistle on 2011-12-11
[SIZE=2]It worked great when I had 11.04, but in 11.10 it's not even working a little.
[/SIZE] [SIZE=3][SIZE=2]
Anyone know how to fix this?
[/SIZE]

[/SIZE]

---

### Post by editheraven on 2011-12-11
Do " cat /etc/modprobe.d/blacklist.conf | grep pcspkr ". If it echoes "blacklist pcspkr" then go and remove/comment that line from blacklist.conf.


Sry. you said internal microphone? i thaught you mean speaker

---

### Post by pretty_whistle on 2011-12-11
That's ok.

---

### Post by pretty_whistle on 2011-12-11
bump

---

### Post by gennatolls on 2011-12-11
Can you go to the sound settings menu then enable your microphone from the input section? I've also used Gnome alsa mixer before to configure things like that when installing Ubuntu on my macbook. Good Luck.

---

### Post by pretty_whistle on 2011-12-11
> **gennatolls said:**
> Can you go to the sound settings menu then enable your microphone from the input section? I've also used Gnome alsa mixer before to configure things like that when installing Ubuntu on my macbook. Good Luck.
I have done that but the mic just isn't working for whatever reason.

P.S.
:D
:D
Still luv your name.

---

### Post by pretty_whistle on 2011-12-12
Anyone know?

---

### Post by pretty_whistle on 2011-12-12
I even tried fixing it installing gnome alsa mixer.  It just isn't working.

The internal mic acts dead.  It's as if I had it on mute.

---

### Post by beric on 2012-03-07
same error here on macbook air 1st gen.

---


---
title: "Sound problems"
date: 2006-02-08
forum: General Help
---

### Post by wilsonisme on 2006-02-08
My sound device is recognized fine, and I hear sound fine. However, when I am hearing it from two sources (ie, playing music and playing america's army at the same time) only one thing gets through! This is always what was opened first. 

Also, XMMS never works when I first open a song with it, I have to press play like three times, clicking out of "Couldn't open audio. Please check that: Your soundcard is configured properly, you have the correct output plugin selected, no other program is blocking the sound card." Like I said, after pressing play about three times it magically works.

What am I doing wrong? I can't imagine linux can't let you, for example, listen to music and play a song at the same time.


Also: I have a ubuntu box at school. The school has a proxy. I set it up in the System>Prefrences>Network Proxy settings, and everything works fine now. However, synaptic still did not work so I had to set up the proxy individually in that program, and it began working. Buttt, the only thing that still doesnt work is when I am installing something manually from the console. Also, automatrix does not work either (I assume for the same reason)

So my questions regarding this is:

1) How do I get the console to behave with the school's proxy?
2) Why is it that doing the "System>Prefrences>Network Proxy settings" did not have a global effect and as such make every program play nice with the proxy? Seems pointless if I set that yet still have to set up the proxy in individual programs (although I admit it did make firefox work out of the box)

---

### Post by wilsonisme on 2006-02-09
Anyone have a solution to either problem?

---

### Post by newuser111 on 2006-02-09
not sure if americas army uses oss or alsa, but ALSA can mix whereas OSS cannot

the idea is to make most applications use alsa wherever possible

and try "killall esd" in a terminal to see if it fixes xmms sound

[http://www.ubuntuforums.org/showthread.php?t=44753&highlight=happy+alsa](http://www.ubuntuforums.org/showthread.php?t=44753&highlight=happy+alsa)

---

### Post by wilsonisme on 2006-02-09
Sounds like windows beats linux hands down in one area: sound... I never had problems with multiple programs playing sound at once when I was on windows  :neutral:.

Anyway, any tips for the console proxy issue?

---


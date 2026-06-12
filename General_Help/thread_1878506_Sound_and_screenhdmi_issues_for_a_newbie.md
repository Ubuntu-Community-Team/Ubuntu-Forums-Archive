---
title: "Sound and screen/hdmi issues for a newbie"
date: 2011-11-09
forum: General Help
---

### Post by timenight113 on 2011-11-09
I used Ubuntu once long ago but didnt learn much about it cause i had someone on hand to help me alot when it broke. This time i am trying to do it all on my own. I built a computer and when i installed 11.04 they computer wouldnt play sound but my video worked on my tv so it turned into another screen for me. Now for some reason the you cant see it on the tv anymore. The only thing i did was update ubuntu and it asked me to install drivers for my video card. Since i have a hdmi with audio i figured that might get my sound working even though my speakers werent playing anything. Now where should i start. Also I tried reformatting  to see if the video would start working and it didnt. I am using a
**[SIZE=2]NVIDIA [/SIZE][SIZE=2][B]ZOTAC ZT-40503-10L GeForce GTS 450 (Fermi) 1GB 128-bit GDDR5 PCI Express 2.0 x16 HDCP Ready SLI Support Video Card**[/SIZE][/B]

---

### Post by papibe on 2011-11-09
Maybe the outputs are muted. Try  [alsamixer]("http://alsa.opensrc.org/Alsamixer"). Check this [tutorial]("http://www.patheticcockroach.com/mpam4/index.php?p=62").

Run it like this:
```
$ alsamixer
```
Unmute the speakers, test them. When you get the results you're going for, save the settings like this:
```
$ alsactl store
```
Hope it helps. Tell us how it goes.
Regards.

---

### Post by timenight113 on 2011-11-11
nope did not work. but i saw that you could switch between video cards on that program cause my video card is supposed to have sound out. I attached it because i couldnt get it to post on the post. 


[ATTACH]206911[/ATTACH]

anymore ideas?

---

### Post by timenight113 on 2011-11-13
bump

---

### Post by timenight113 on 2011-11-14
sound issue solved.

---

### Post by papibe on 2011-11-15
How did you solve it?

It could be useful for other people with the same problem.

Regards.

---


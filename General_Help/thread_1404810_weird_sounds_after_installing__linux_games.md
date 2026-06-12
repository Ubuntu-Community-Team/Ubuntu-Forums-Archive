---
title: "weird sounds after installing  linux games"
date: 2010-02-11
forum: General Help
---

### Post by ontherooftop on 2010-02-11
Ever since I downloaded some linux games I have some games that are 
fine and other games have no sound or have really weird buzzing noises
off and on while playing with music on. Also I hear a pop noise
from my speaker every now and then ever since I downloaded these
Linux games from the package manager. I also even tried disabling 
the operating system sounds and startup sound with no luck, any
ideas?

---

### Post by NightwishFan on 2010-02-11
Some SDL games need libsdl1.2debian-pulseaudio instead of alsa.
[Click To Install]("apt://libsdl1.2debian-pulseaudio")

(This is not a 3rd party link, it just installs from Ubuntu respositories)

---

### Post by ontherooftop on 2010-02-11
I tried and it's asking to run with an application and I don't know
what to do, Is there something in synaptic that can solve this or in
terminal because I know I am using alsa.

---

### Post by NightwishFan on 2010-02-11
If you have the latest Ubuntu, pulseaudio should be installed. Just hit "Ok" for the link if gave you, it will install automatically. If you do not want it of it does not work, just search for libsdl1.2debian-pulseaudio or run:
```
sudo aptitude install libsdl1.2debian-pulseaudio
```

Are you using 9.10 Karmic?

---

### Post by ontherooftop on 2010-02-11
found it in package manager and so far no popping noises for a few minutes
so far so good , thanks, I will test the games tomorrow. I am using
ubuntu 9.10 with compiz pimped out to make Linux the best eye candy OS,

---

### Post by NightwishFan on 2010-02-11
Enjoy! Doing this fixed sound for me in Urban Terror.

---

### Post by ontherooftop on 2010-02-11
didn't work sounds are still weird. is there a alternative to alsa?
I had this problem on a different ubuntu distro and turning off operating
sounds helped or using OSS, I dont know how to do that anymore or is there
a better solution.

---

### Post by NightwishFan on 2010-02-11
What exact game? My fix only works for sdl games.

---

### Post by ontherooftop on 2010-02-11
like supertux2, tux kart racer has the strange sounds, and viruskiller
has no sound at all, I downloaded a lot so I know there are more, 
lincity, extremetuxracer, tomatoes works fine.

---

### Post by NightwishFan on 2010-02-11
I think supertux2 uses sdl. Try rebooting, and seeing if that helps. If not, I will try to get back to you if I find something but I am not sure.

---

### Post by ontherooftop on 2010-02-11
thanks i made my ubuntu look awesome with the features that 
can make windows fanboys crap their pants and even converted 
people, but i hopefully will fix this tomorrow as i did way too
much today.

---


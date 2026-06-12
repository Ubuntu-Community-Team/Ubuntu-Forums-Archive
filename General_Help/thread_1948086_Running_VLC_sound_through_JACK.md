---
title: "Running VLC sound through JACK"
date: 2012-03-27
forum: General Help
---

### Post by sirriffsalot on 2012-03-27
Hey all!

I'm having difficulty finding an effective/functional/updated way of running the VLC audio through JACK, which would be immensely handy for someone who does a lot of musical production. Any ideas or links?:)

Thanks for your time!

--> Leo

P.S. Using Ubuntu Studio by the way

---

### Post by Yellow Pasque on 2012-03-27
```
sudo apt-get install vlc-plugin-jack
```
Then choose JACK output in VLC preference (or use --aout jack from command-line).

---

### Post by sirriffsalot on 2012-03-29
Well I've gotten that far, but I frankly have no clue how to setup JACK in relation to VLC. When I try to start jack I just get the usual error messages; I'm quite new to JACK and have no idea how it should be set up to work with VLC, haha:)

Thanks for your time!!

Edit: I've found out how, since there is sound coming, but real laggy and uncomfortable sound, so obviously I'm doing something wrong. Would you mind taking me through what you were saying I should do step by step, or directing me to somewhere that does?:) You'll obviously need some info on what my settings are in JACK, and probably more, so ask away if you have to!

Cheers!

---

### Post by Yellow Pasque on 2012-03-29
I personally don't use jack...

---

### Post by sirriffsalot on 2012-03-29
Lol, well thanks anyway:D

bump to everyone else!!:)

---

### Post by sirriffsalot on 2012-04-08
Alright, figured it out in the end. Either, you can go into the connections page in JACK and connect things as appropriate, or read about the Patchbay option in JACK which does this automatically when VLC is started so you won't have to connect it yourself every time you start JACK. Best of luck!

--> Leo

Edit: This is presuming you have the "vlc-plugin-jack" installed and selected in VLC as the output: Preferences > Sound > Output module > select JACK audio output and do as instructed above. Best of luck!

---


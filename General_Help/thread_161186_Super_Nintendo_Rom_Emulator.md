---
title: "Super Nintendo Rom Emulator?"
date: 2006-04-16
forum: General Help
---

### Post by truNWA on 2006-04-16
Does anyone know a SNES rom emulator for linux? If so culd you link me to it and  a guide on howto use it, if there is one.

---

### Post by Azrael on 2006-04-16
[quote=truNWA]Does anyone know a SNES rom emulator for linux? If so culd you link me to it and a guide on howto use it, if there is one.[/quote] Both zsnes and snes9x have a linux port (which you can see for yourself by doing *sudo apt-cache search snes* in a terminal if you have the multiverse repositories enabled).

---

### Post by xXx 0wn3d xXx on 2006-04-16
[QUOTE=truNWA]Does anyone know a SNES rom emulator for linux? If so culd you link me to it and  a guide on howto use it, if there is one.[/QUOTE]
Yes, snes9x, zsnes, and xmess-x are avaible in the repositories all are snes emulators except for xmess-x which supports many different consoles/systems. Search for them in synaptic or in terminal type:

> sudo apt-get update 

then 
> 
sudo apt-get install <emulator name here, get them from above>

Example: "sudo apt-get install snesemu"   <= Don't use quotes.


Don't use the <> symbols.

---

### Post by jworr on 2006-04-16
I highly recommend zsnes, it is full featured and works very well, I use it all the time to play mega man x and super mario world

to install:

sudo apt-get install zsnes

---

### Post by Sonique on 2006-04-17
I use ZSNES since I used to use it on windows, and it works fine, use that.

---

### Post by pengko.eo on 2008-05-11
hello. ive downloaded znes successfully. the thing is when i play games, there is no sound. can anyone help me out on this? thanks

---

### Post by pengko.eo on 2008-05-11
please help me. playing games without sound is a torture. thanks guys

---

### Post by erginemr on 2008-05-11
ZSnes is indeed a fantastic emulator (also as was SNES a fatastic console), but there is a well-known sound issue in Hardy with default ZSnes settings. To overcome that problem:

(1) From a terminal, open the zsnes config file:
```
gedit ~/.zsnes/zsnesl.cfg
```

(2) Find the lines:
```
;  ----
; -- Sound --
;  ----

; libAO driver to use. Use zsnes --help to see valid list.
; However "auto" (to automatically pick best one), and "sdl" should
; always be available.
libAoDriver="auto"
```

(3) Change "auto" to "sdl", so that it reads:
```
libAoDriver="sdl"
```

Now, you should have sound.

---

### Post by erginemr on 2008-05-11
Once you fix that problem, if you happen to experience crackling sound in ZSnes games, you can try this fix that involves putting an ALSA config file (.asounrc) into your home folder:

[http://ubuntuforums.org/showpost.php?p=4177459&postcount=9](http://ubuntuforums.org/showpost.php?p=4177459&postcount=9) (refer to item #6)

---

### Post by Chonnawonga on 2008-05-11
Works great for me! Thank you!

---


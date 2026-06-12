---
title: "Tried to upgrade Realtek ALC888 drivers, now cannot detect ANY sound card"
date: 2011-07-04
forum: General Help
---

### Post by DJCatnip on 2011-07-04
I'm using Xubuntu Natty at the moment, on an Acer Aspire 5739G. Figured I would go to Realtek's site and get [the most recent soundcard driver]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false"), since the built-in subwoofer has never worked on Linux for me.

I used the automatic install script, then when it tried to probe for other devices, suddenly I had no sound.

I'm currently getting

```
korin@corrosion:~$ aplay -l
aplay: device_list:240: no soundcards found...
```

I tried reinstalling the ALSA driver, but to no avail. I now have no sound, and no idea a) why this failed, and b) how to fix it.

Any help would be REALLY appreciated. :(

---

### Post by DJCatnip on 2011-07-04
```
korin@corrosion:~$ lsmod | grep snd
snd_page_alloc         18484  0 
korin@corrosion:~$ alsamixer 
cannot open mixer: No such file or directory
korin@corrosion:~$ ls /dev/snd/
seq  timer

```

Doesn't really fill me with confidence either.

---

### Post by DJCatnip on 2011-07-04
Additionally, there doesn't seem to be a /proc/asound at all. :|

---

### Post by DJCatnip on 2011-07-06
Okay, well, I'm not going to mark this as "solved", but it seemed we couldn't do anything really to fix this. A reinstall of the OS fixed it, as you can imagine.

This is the second time I've had issues from Realtek's drivers, so all I can suggest is **avoid using the Unix HDA sound drivers from Realtek's site unless you REALLY know what you're doing**.

---


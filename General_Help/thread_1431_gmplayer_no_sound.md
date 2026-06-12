---
title: "gmplayer: no sound"
date: 2004-10-20
forum: General Help
---

### Post by Neo40 on 2004-10-20
Hi,

I just installed Ubuntu this evening. First thing I did: I tried to play some movies with totem but it dies every time. Then, I followed  the wiki to install Mplayer. No problem to install it. I can play movies but I don't have any sound! 
However, I have sound when gnome open up in gdm session...

If I do a "mplayer -ao help" I get this:
..
..
Available audio output drivers:
        mpegpes DVB audio output
        oss     OSS/ioctl audio output
        null    Null audio output
        pcm     RAW PCM/WAVE file writer audio output
        plugin  Plugin audio output

Why Alsa is not there??  I nerver had problem with sound with others distro like Slackware or Archlinux....

Thanks.

---

### Post by Neo40 on 2004-10-21
To answer myself: I had to install totem-xine to be able  to see movies with totem. And sound is working too!

---

### Post by kingmob on 2004-10-21
So now you can select alsa in mplayer?
Asking this because i have the exact same problem :(

---

### Post by Neo40 on 2004-10-21
[quote=kingmob]So now you can select alsa in mplayer?
Asking this because i have the exact same problem :([/quote]

No, I can't.

---

### Post by kingmob on 2004-10-21
So, any ideas as to how this comes and how it should be solved?
It seems to be Unbuntu related, as i didn't have these problems before.

---

### Post by kingmob on 2004-10-21
Solved it by apt-getting libasound2-dev and reconfiguring mplayer. It had not autodetected alsa correctly.

---

### Post by im_ka on 2004-10-21
[quote=kingmob]So now you can select alsa in mplayer?
Asking this because i have the exact same problem :([/quote]

i've had an annoying, continous cracking niose  when using alsa. oss works fine  for me

---


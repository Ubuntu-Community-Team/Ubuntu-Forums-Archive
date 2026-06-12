---
title: "TV-Fox"
date: 2010-03-09
forum: General Help
---

### Post by JugglinPhil on 2010-03-09
Hi, I just installed the TV-Fox add-on for Firefox ([https://addons.mozilla.org/en-US/firefox/addon/11200](https://addons.mozilla.org/en-US/firefox/addon/11200)), but it doesn't seem to work. When I choose a Channel all it does is load for ages, saying 'waiting for video'. Are there any additional packages that need to be installed for this to work, or is it just not working in general?

---

### Post by 2hot6ft2 on 2010-03-09
Did you read and follow the instructions on the plugin page you linked to?
> For Unix users:
Our TV-FOX streams are compatible with Unix
We tested our streams using the Mplayer plugin on:
- Gentoo Linux 1.5.1
- FreeBSD 5.x
[http://www.mplayerhq.hu/design7/dload.html](http://www.mplayerhq.hu/design7/dload.html)

Mplayer tends to take longer to connect and buffer the stream
than Windows Media player, so please be patient.
To reduce the buffering time in mplayer, update /etc/mplayerplug-in.conf by uncommenting the following line:
cachesize=256

---

### Post by 2hot6ft2 on 2010-03-09
Seems to work ok. The Mplayer plugin is no longer supported and is now replaced with gecko-mediaplayer.
First remove the Mplayer plugin
```
sudo apt-get remove mozilla-mplayer
```
Then install Gecko Media Player.
```
sudo apt-get install gecko-mediaplayer
```
Edit the file as recommended
```
gksu gedit /etc/mplayerplug-in.conf
```
changing
> #cachesize=512
to
> cachesize=512
save and close
close firefox then open it again.

If there's a channel that doesn't work report it using the red link in the top left of the display.

---

### Post by Maheriano on 2010-03-09
Juggle-World doesn't sound like it's in the USA. I'm pretty sure this plugin won't work outside the country.

---

### Post by 2hot6ft2 on 2010-03-09
> **Maheriano said:**
> Juggle-World doesn't sound like it's in the USA. I'm pretty sure this plugin won't work outside the country.
It has a lot of Countries listed. I'll try a some and post back in a few.

Let's see I got
Disco Russia
ClapTV France
Sat 7 Kids Egypt
HipHop TV Bulgaria

So I would say it doesn't matter....lol this is kinda cool.
P.S. I'm in the USA

---

### Post by JugglinPhil on 2010-03-09
Hi thanks a lot for the quick reply, I followed all your instructions, however it still doesn't seem to work for me. Maybe it is restricted to USA only, and yes, Juggle-World is indeed not in the States. ;)

---

### Post by zissshh on 2010-07-23
i have vlc player as default player for mms steraming and wmp.,,,now why does this fox tv window is not directed to vlc

---


---
title: "DVD plugins for 10.04LTS"
date: 2011-01-30
forum: General Help
---

### Post by the wolfe on 2011-01-30
I need to locate the plugins to play DVD movies in 10.04. 
I already tried what I used on another computer which was: "sudo apt-get install libdvdread4" and "sudo/usr/share/doc/libdvdread4/install-css.sh". Installed both and then restarted, but Movie Player still says that it needs the DVD plugin. So... what is the right plugins for the 10.04 Movie Player?

---

### Post by OldBoy44 on 2011-01-30
Hi,

It is a bit crude but codecs and command are on page 90 of the manual at -
   [http://ubuntu-manual.org/](http://ubuntu-manual.org/)

Cheers,

---

### Post by the wolfe on 2011-01-30
the plugins listed there did not work. Thats where I got the first code that I installed.

---

### Post by OldBoy44 on 2011-01-30
They worked for me -

Did you also enter command -

```
$ sudo /usr/share/doc/libdvdread4/install-css.sh 
```As well as the 9 plugins?

---

### Post by mc4man on 2011-01-30
try installing the basic gstreamer decoding plugins
```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad \
gstreamer0.10-plugins-ugly
```

(you may find vlc a bit better at dvd movie playback and navigation

---

### Post by jimmers on 2011-01-30
Hi,
You have not said what App, you are trying to play DVD's, I use Kaffeine with gxine installed, W32 codecs and ubuntu-restricted-extras, and have no probs watching dvd's

Try

Luck

---

### Post by the wolfe on 2011-01-30
> **jimmers said:**
> Hi,
You have not said what App, you are trying to play DVD's, I use Kaffeine with gxine installed, W32 codecs and ubuntu-restricted-extras, and have no probs watching dvd's

Try

Luck
I am currently installing Ubuntu Restricted Extras, but the below quoted code has started the dvd availability. thanks for the help though. 

> **mc4man said:**
> try installing the basic gstreamer decoding plugins
```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad \
gstreamer0.10-plugins-ugly
```

(you may find vlc a bit better at dvd movie playback and navigationThanks man.That code worked fine. I use Movie simply because it is the default (like Windows Media Center under windows XP). But thanks for the suggestion to use VLC.

---


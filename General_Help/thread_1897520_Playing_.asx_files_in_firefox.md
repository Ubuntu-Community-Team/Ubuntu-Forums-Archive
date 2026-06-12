---
title: "Playing .asx files in firefox"
date: 2011-12-19
forum: General Help
---

### Post by flyingfisch on 2011-12-19
How do I get .asx files to play in firefox? I tried installing VLC, but it still doesn't work. Whenever I try to play the file, firefox crashes.

---

### Post by flyingfisch on 2011-12-19
bump.

---

### Post by hansdown on 2011-12-19
Hi, flyingfisch.

Mplayer works.

```
sudo apt-get install mplayer
```

```
sudo apt-get install mozilla-mplayer
```

If you have the multiverse repos enabled.

---

### Post by flyingfisch on 2011-12-20
> **hansdown said:**
> ...
If you have the multiverse repos enabled.

What are those?

---

### Post by lovinglinux on 2011-12-20
> **flyingfisch said:**
> What are those?

Those are installation commands. The first one is the Mplayer backend, which is a powerful media player. The second one is the plugin that uses Mplayer. In fact, the second command is incorrect, since mozilla-mplayer is now gecko-mediaplayer. So the correct command is:

```
sudo apt-get install gecko-mediaplayer
```

If you are not familiar with command-line, you can install from the Software Center. Just launch it and type *gecko-mediaplayer* in the search.

---

### Post by flyingfisch on 2011-12-20
thx, but what i meant was, what are "multiverse repos"?

---

### Post by hansdown on 2011-12-20
> **flyingfisch said:**
> thx, but what i meant was, what are "multiverse repos"?

Sorry, flyingfisch.

Software sources allows you to install certain extra packages.

lovinglinux has a very good suggestion, for

```
gecko-mediaplayer
```

---

### Post by monadikimagapi on 2012-04-23
Hi all,

In case someone else have the same question, [this]("http://askubuntu.com/questions/113411/chrome-embed-vlc-player-couldnt-playback-mp4") post was very helpful for me. I am using Ubuntu 11.10 with chromium.

---

### Post by suoshao on 2012-04-23
What are those?[IMG]http://www.keyforex.info/dvd.gif[/IMG]

---

### Post by lovinglinux on 2012-04-23
> **monadikimagapi said:**
> Hi all,

In case someone else have the same question, [this]("http://askubuntu.com/questions/113411/chrome-embed-vlc-player-couldnt-playback-mp4") post was very helpful for me. I am using Ubuntu 11.10 with chromium.

VLC is not a good plugin.

---

### Post by techsupport on 2012-04-23
> **monadikimagapi said:**
> Hi all,

In case someone else have the same question, [this]("http://askubuntu.com/questions/113411/chrome-embed-vlc-player-couldnt-playback-mp4") post was very helpful for me. I am using Ubuntu 11.10 with chromium.

You need to use a guide to make sure you have all the right codecs installed.. 

Use this list to double check everything:

[http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)

---

### Post by hansdown on 2012-04-24
> **lovinglinux said:**
> VLC is not a good plugin.

I tend to agree.

---


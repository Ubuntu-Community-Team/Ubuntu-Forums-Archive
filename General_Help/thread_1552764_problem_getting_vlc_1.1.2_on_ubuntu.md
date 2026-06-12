---
title: "problem getting vlc 1.1.2 on ubuntu"
date: 2010-08-14
forum: General Help
---

### Post by rahilm on 2010-08-14
i have ubuntu lucid 64 bit installed on my laptop. and i want to install the latest vlc player 1.1.2... but the website says that you have to install it manually. how do to that?

i have been using the korn repository on my pc. i tried getting that but the repository doesn't add. it goves the error:

[/code]
sudo add-apt-repository ppa:c-korn/vlc
Error: can't find signing_key_fingerprint at [https://launchpad.net/api/1.0/~c-korn/+archive/vlc](https://launchpad.net/api/1.0/~c-korn/+archive/vlc)
[/code]


Is it possible to get the latest vlc on ubuntu??

---

### Post by alenis on 2010-08-14
It seems VLC is no longer there:

[https://launchpad.net/~c-korn/+archive/ppa/+packages]("https://launchpad.net/~c-korn/+archive/ppa/+packages")

---

### Post by rahilm on 2010-08-14
> **alenis said:**
> It seems VLC is no longer there:

[https://launchpad.net/~c-korn/+archive/ppa/+packages]("https://launchpad.net/%7Ec-korn/+archive/ppa/+packages")
NOOOOOOOOO!!!
*panic*  will hav to use old one now,,,....

---

### Post by dream_w on 2010-08-14
Why don't you download the source [from here]("http://www.videolan.org/vlc/download-sources.html") and build it? I think all you need is a relatively recent [fox-toolkit]("http://www.fox-toolkit.org/download.html"), version 1.6 or higher will do it.

---

### Post by rahilm on 2010-08-14
> **dream_w said:**
> Why don't you download the source [from here]("http://www.videolan.org/vlc/download-sources.html") and build it? I think all you need is a relatively recent [fox-toolkit]("http://www.fox-toolkit.org/download.html"), version 1.6 or higher will do it.
working on it

---

### Post by JohnnyC35 on 2010-08-14
I tried installing it from [http://ppa.launchpad.net/nvidia-vdpau/cutting-edge-multimedia/ubuntu/](http://ppa.launchpad.net/nvidia-vdpau/cutting-edge-multimedia/ubuntu/) lucid/main
apt-get update, upgrade
install vlc succeeded and then

vlc: error while loading shared libraries: libvlccore.so.5: cannot open shared object file: No such file or directory

looking into

found the issue. I had a ppa with an older vlc  'ppa:ferramroberto/lucidtest' after removing that I removed and  reinstalled vlc. now have 1.2 from nvidia-vdpau/... :D

---

### Post by LnRSoft on 2010-08-14
Cheers Mate!

[http://ppa.launchpad.net/nvidia-vdpau/cutting-edge-multimedia/ubuntu/](http://ppa.launchpad.net/nvidia-vdpau/cutting-edge-multimedia/ubuntu/) 
worked for me :popcorn:

---

### Post by rahilm on 2010-08-15
it is asking for a partial upgrade... only to double check .. is it safe??
i did a partial upgrade once and 60% of apps stopped working..

---

### Post by praveenmarkandu on 2010-08-15
tried to challenge myself by compiling it from source. managed to make a deb but when i run vlc i get ```
 vlc: error while loading shared libraries: libvlccore.so.5: cannot open shared object file: No such file or directory
```

so im going about the easy way and using the ppa provided above ^

---

### Post by andrew.46 on 2010-08-18
I run a quite complex guide that deals with compiling the development version of vlc but in response to the trouble many Lucid users are having I have added a small section that shows how to build vlc 1.1.2 from source:

Howto: Build the development version of vlc under Ubuntu
[http://ubuntuforums.org/showthread.php?t=1398119](http://ubuntuforums.org/showthread.php?t=1398119)

It is quite an involved guide but if followed carefully will give you a very fully-featured copy of vlc. Definitely not the same as adding a PPA though...

Andrew

---

### Post by praveenmarkandu on 2010-08-18
> **andrew.46 said:**
> I run a quite complex guide that deals with compiling the development version of vlc but in response to the trouble many Lucid users are having I have added a small section that shows how to build vlc 1.1.2 from source:

Howto: Build the development version of vlc under Ubuntu
[http://ubuntuforums.org/showthread.php?t=1398119](http://ubuntuforums.org/showthread.php?t=1398119)

It is quite an involved guide but if followed carefully will give you a very fully-featured copy of vlc. Definitely not the same as adding a PPA though...

Andrew

i managed to do it. found out libraries were installed in /usr/local/lib instead of /usr/lib. have to run:

```
sudo ln -s /usr/local/lib/libvlc* /usr/lib/
sudo ln -s /usr/local/lib/libx264.a /usr/lib/
sudo ln -s /usr/local/lib/vlc /usr/lib/vlc
```

---

### Post by mc4man on 2010-08-18
> i managed to do it. found out libraries were installed in /usr/local/lib instead of /usr/lib. have to run:
......


If you're happy with what you have that's ok, but you should never have had to do that.
Most likely caused by having some vlc libraires installed during the build or still installed now.
(or some flaw in your build/packaging method

---


---
title: "Despotify"
date: 2011-04-13
forum: General Help
---

### Post by xic816 on 2011-04-13
Is despotify legit, if so how to install?

R

---

### Post by Enigmapond on 2011-04-13
It's legit but I think you will need to compile it as it's not packaged anywhere I can fine:

```
sudo apt-get install libssl-dev zlib1g-dev libvorbis-dev libpulse-dev libexpat1-dev libncurses5-dev
wget http://downloads.sourceforge.net/despotify/despotify-r761.tar.gz?use_mirror=freefr
tar xvf despotify-r761.tar.gz
cd despotify-r761/
make
./despotify
```

Note: these instructions are 2 years old.

---

### Post by xic816 on 2011-04-14
> **Enigmapond said:**
> It's legit but I think you will need to compile it as it's not packaged anywhere I can fine:

```
sudo apt-get install libssl-dev zlib1g-dev libvorbis-dev libpulse-dev libexpat1-dev libncurses5-dev
wget http://downloads.sourceforge.net/despotify/despotify-r761.tar.gz?use_mirror=freefr
tar xvf despotify-r761.tar.gz
cd despotify-r761/
make
./despotify
```Note: these instructions are 2 years old.

Did u have a look at [http://despotify.se/source-code/](http://despotify.se/source-code/) , found the source code (whatever that means) and btw; whats the differance between despotify-simple and despotify? At the specs on their site it seems to be the possibility to make play list's but wasn't there a problem with the playlist's in despotify, something about relieving personal information? 

Another question; when there are programs like this one which says it needs f. example; You’ll need [OpenSSL]("http://www.openssl.org/"), [zlib]("http://www.zlib.net/"), [libvorbis]("http://www.xiph.org/vorbis/") and one of the packages to support the audio backends
what does that mean? I'm used to windows when u just install the program, thats it..

Thanks

---


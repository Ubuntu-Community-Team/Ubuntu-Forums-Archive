---
title: "How to get System Sounds with only OSS"
date: 2009-11-26
forum: General Help
---

### Post by otchie1 on 2009-11-26
I haven't used ALSA in about a decade and I never saw the need for Pulse as OSS does everything I want. Seems Ubuntu devs do use Pulse though as with it removed you lose your system sounds.

To get them back you need a recent version of libcanberra and this is how to do it.

Assuming you have already cleansed ALSA & Pulse from your box AND added gstreamer AND enabled sounds using the old gnome-sound-preferences as detailed under Google and as per the Wiki then all you need to do is to get and compile libcanberra-0.18

Get it from the [here]("http://0pointer.de/lennart/projects/libcanberra/libcanberra-0.18.tar.gz").

you will probably need to add some libraries to correctly compile the code,
```
sudo apt-get install libvorbis-1.2.3 libtool libvorbisfile3
```
and maybe some others but error codes will point you in the right direction if you lack anything. Unwrap libcanberra with
```
tar xvzf libcanberra-0.18.tar.gz
```

then
```
cd libcanberra-0.18
./configure --disable-alsa --disable--pulse --enable-gstreamer
make
sudo make install
```

that puts the new library in /usr/local/lib although that can be configured to put it straight in /usr/lib instead if you want.
I just,
```
cd /usr/lib
sudo mv libcanberra-0.15 libcanberra-0.15-OLD
cd /usr/local/lib
sudo cp libcan* /usr/lib/ -r
cd /usr/lib
sudo ln -s libcanberra-0.18 libcanberra-0.15
```

log out and you should be done.

---


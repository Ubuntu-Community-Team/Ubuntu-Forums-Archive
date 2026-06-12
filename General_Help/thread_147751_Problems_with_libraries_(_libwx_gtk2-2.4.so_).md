---
title: "Problems with libraries ( libwx_gtk2-2.4.so )"
date: 2006-03-20
forum: General Help
---

### Post by BitTorrentBuddha on 2006-03-20
Okay, I have this program I'm trying to install, [archivist](archivist.sourceforge.net), and when I try to run the included binary, I get ```
./archivist: error while loading shared libraries: libwx_gtk2-2.4.so: cannot open shared object file: No such file or directory
``` where can I go about obtaining libwx_gtk2-2.4.so? (It's not any of the standard ones in synaptic, perhaps a dev one?)

---

### Post by BitTorrentBuddha on 2006-03-21
bump :(

---

### Post by Ramses de Norre on 2006-03-21
sudo apt-get install libwxbase2.4-1

---

### Post by BitTorrentBuddha on 2006-03-21
same error

---

### Post by BitTorrentBuddha on 2006-03-22
bump

---

### Post by Ramses de Norre on 2006-03-22
Did you have to compile the program? If so, did ./configure said everything was ok?
If not: I don't really know where to get the library, the one I gave you was the only one in the repo's..

---

### Post by Ramses de Norre on 2006-03-22
```
sudo -s
apt-get install auto-apt
auto-apt update
auto-apt updatedb
auto-apt update-local
auto-apt run ./archivist
```
This may work, but I never used it like this before. (if the script you're trying to run isn't ./archive you should change it in the last line.)

---

### Post by BitTorrentBuddha on 2006-03-22
there was no compiling to be done, it comes as a binary with the tarball

---

### Post by BitTorrentBuddha on 2006-03-22
auto-apt isn't in any repos I have either

---

### Post by BitTorrentBuddha on 2006-03-23
found auto-apt, followed the instructions, got the same error ```
./archivist: error while loading shared libraries: libwx_gtk2-2.4.so: cannot open shared object file: No such file or directory
```

---

### Post by BitTorrentBuddha on 2006-03-24
bump

---

### Post by BitTorrentBuddha on 2006-03-24
bump

---

### Post by BitTorrentBuddha on 2006-03-24
Okay, can anyone at least tell me where I would have to put libwx_gtk2-2.4.so for it to load properly?

---

### Post by BitTorrentBuddha on 2006-03-25
bump](*,)

---

### Post by BitTorrentBuddha on 2006-03-26
pbmu

---

### Post by Ramses de Norre on 2006-03-26
Most of the *.so files on my system are in /usr/lib/ 
Have you found the file?

---

### Post by BitTorrentBuddha on 2006-03-26
no, but i did find [this]("http://waaaghtv.gamesports.de/index.php?board=6;action=display;threadid=78") thread which seems to describe the exact same problem, and they concluded that the debian packages didn't work for libwx_gtk2-2.4.so

---


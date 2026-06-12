---
title: "Help with shell scripts"
date: 2009-07-14
forum: General Help
---

### Post by frt975 on 2009-07-14
```
#!/bin/bash
#conpile and install

echo "What is the path of the program you want to install?"
read path
cd $path
./configure --prefix=/usr
make
sudo make install
```I want the script to wait for the previous line to finish **than** execute the next line.
Thanks

---

### Post by nikhilk on 2009-07-14
> **frt975 said:**
> I want the script to wait for the previous line to finish **than** execute the next line.

It seems that this is what should happen. Have seen any specific line which begins execution before the earlier line finishes?

---

### Post by Zeratul021 on 2009-07-14
Definitely, programs/scripts are sequential until they use more threads or processes (no fork or exec here).

---

### Post by frt975 on 2009-07-14
[FONT=Arial][SIZE=2]I'm trying to co[/SIZE][/FONT][FONT=Arial][SIZE=2]mpile and install[/SIZE][/FONT] Audacity as my test app.
The terminal tells me this
```
[SIZE=1]What is the path of the program you want to install?
/home/frt975/Desktop/audacity-src-copy).2.6
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking whether gcc needs -traditional... ^Ano
checking for g++... g++
checking whether we are using the GNU C++ compiler... ^A^A^A^Ayes
checking whether g++ accepts -g... ^Ayes
checking how to run the C++ preprocessor... g++ -E
checking for a BSD-compatible install... /usr/bin/install -c
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking sndfile.h usability... no
checking sndfile.h presence... no
checking for sndfile.h... no
checking for lib-src/libmad/frame.h... no
checking for lib-src/libvorbis/include/vorbis/vorbisenc.h... no
checking for lib-src/libid3tag/frame.h... no
checking for lib-src/libsamplerate/src/samplerate.h... no
checking for lib-src/libresample/include/libresample.h... yes
checking for lib-src/soundtouch/include/SoundTouch.h... yes
checking for lib-src/libflac/include/FLAC/all.h... no
checking mad.h usability... no
checking mad.h presence... no
checking for mad.h... no
checking vorbis/vorbisenc.h usability... no
checking vorbis/vorbisenc.h presence... no
checking for vorbis/vorbisenc.h... no
checking id3tag.h usability... no
checking id3tag.h presence... no
checking for id3tag.h... no
checking FLAC/all.h usability... no
checking FLAC/all.h presence... no
checking for FLAC/all.h... no
--- Configuring soundtouch
--- Configuring libsndfile
--- Configuring libresample
checking for zip... /usr/bin/zip
checking for wx-config... no
configure: error: "Could not find wx-config: is wxWidgets installed? is wx-config in your path?"
make: *** No targets specified and no makefile found.  Stop.
[sudo] password for frt975:
No makefile found 
[/SIZE]
```
I the the makefile part was there but it quit right after I saw it.
[B][FONT=Arial][SIZE=2]
[/SIZE][/FONT][/B]

---

### Post by nikhilk on 2009-07-14
From the output you have pasted it seems that make did not run successfully due to the error below
```
configure: error: "Could not find wx-config: is wxWidgets installed? is wx-config in your path?"
```
It seems you do not have wxWidgets installed. Try installing it and make should complete just fine.
The commands in your script are executing sequentially, it is just that one of them has failed (make) and since the next one depends on it (sudo make install) it failed as well.
Instead of putting the two make commands on separate lines, put them together like this
```
make && sudo make install
```
The '&&' ensures that unless the first command ran successfully, the next command is not run.

---

### Post by frt975 on 2009-07-14
I installed wxWidgets but now it just quits without asking for my password. :sad:

---

### Post by nikhilk on 2009-07-14
> **frt975 said:**
> I installed wxWidgets but now it just quits without asking for my password. :sad:

Could you post the output of the make run after installing wxWidgets?

---

### Post by frt975 on 2009-07-14
> **nikhilk said:**
> Could you post the output of the make run after installing wxWidgets?
What do you mean by that?

---

### Post by nikhilk on 2009-07-14
> **frt975 said:**
> What do you mean by that?

Could you post the output of your script like you did the last time (with the wxWidgets error)?

---

### Post by frt975 on 2009-07-14
It stops too quickly for me to copy and paste. Is there some kind of setting in terminal that saves the result to a file?

---

### Post by t4thfavor on 2009-07-14
./script.sh >> file.log
will get you a file.log in the current directory.

---

### Post by sisco311 on 2009-07-14
just install the dependencies:
```
sudo apt-get build-dep audacity
```


and edit your script to something like this: 
```
...
./configure || exit 1
make && sudo make install
...
```

---

### Post by frt975 on 2009-07-14
Here

---

### Post by frt975 on 2009-07-14
I tried Add/remove programs and audicoy was there. Yay.:p Thanks for telling me how to improve my script

---


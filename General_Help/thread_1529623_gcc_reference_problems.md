---
title: "gcc reference problems"
date: 2010-07-12
forum: General Help
---

### Post by plypencil on 2010-07-12
I am trying to compile a program called The Powder Toy (v35.0) (download link [http://powder.hardwired.org.uk/Download/powder-35.0-src.zip](http://powder.hardwired.org.uk/Download/powder-35.0-src.zip)). It is written in C and has previously been compiled for Linux so the problem is to do with me.

When I try to compile ```
gcc -o powder powder.c
``` I first got errors saying SDL and bzlib.h were missing. So I downloaded the necessary files and installed them. I now have a whole load of errors from the SDL file saying things have been used before referencing.

I understand this may be a simple problem however despite what I search for on programming sites and watching lots of C compiling tutorials I cannot find a solution.

---

### Post by Krisando on 2010-07-12
I had the missing header error, which turned out to be unpacked/compiled or w/e GCC files. A terminal command line to do so fixed my problem. =\ Can't remember command sorry.

---

### Post by marshmallow1304 on 2010-07-12
The file to which you linked has a makefile but no configure file, which means that you just need to cd to the directory and type
```
make
```
which will automatically compile the program.  It spit out a lot of warnings for me, but it still worked.  Then type
```
./powder
```
to run it.

---

### Post by plypencil on 2010-07-12
Thanks for the speedy response.

Marshmallow1304, I did as you said however I get an error and the compilation fails.
```
/usr/bin/ld: cannot find -lbz2
collect2: ld returned 1 exit status
make: *** [powder] Error 1

```

---

### Post by dragos240 on 2010-07-12
Did you install those packages' dev files?

---

### Post by plypencil on 2010-07-12
Yes I did, had to use sudo to copy the files over for the bzlib, the SDL automatically installed. I will try copying the bzlib ones again, check I have not missed any

---

### Post by dragos240 on 2010-07-12
> **plypencil said:**
> Yes I did, had to use sudo to copy the files over for the bzlib, the SDL automatically installed. I will try copying the bzlib ones again, check I have not missed any

Okay. I see the issue here. It's recommended to use the ubuntu repo for these things, try searching synaptic for sdl and bzlib, search for anything ending in -dev or -devel.

---

### Post by plypencil on 2010-07-12
SDL was already done through Synaptic, I cannot find bzlib on it though.

---

### Post by dragos240 on 2010-07-12
> **plypencil said:**
> SDL was already done through Synaptic, I cannot find bzlib on it though.

You can try to find a ppa, it's a bit safer. If you can't find a source, I'll help you, but the last thing you want to do is that on a binary system.

---

### Post by plypencil on 2010-07-12
Im sorry but I dont know what a PPA is?

---

### Post by marshmallow1304 on 2010-07-12
Try installing [libbz2-dev]("apt://libbz2-dev").

---

### Post by plypencil on 2010-07-12
Thanks that fixed it. It has compiled successfully and now runs. Is that package a parent to what I needed?

---


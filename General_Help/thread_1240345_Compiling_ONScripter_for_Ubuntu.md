---
title: "Compiling ONScripter for Ubuntu"
date: 2009-08-14
forum: General Help
---

### Post by Yanatsu on 2009-08-14
Well, I'm aware that there's an ONScripter package that I can just apt-get, but I need to use a patched version and compile it myself. However, even after trying everything I could find on Google, I still can't compile it, and always get the same errors.
```
sean@sean-laptop:~/Desktop/onscripter-20060724-insani$ make -f Makefile.Linux.insani
g++  -O3 -Wall -fomit-frame-pointer -pipe -c `sdl-config --cflags` `smpeg-config --cflags` -DLINUX -DUSE_OGG_VORBIS -DENABLE_1BYTE_CHAR -DFORCE_1BYTE_CHAR -DINSANI onscripter.cpp
/bin/sh: smpeg-config: not found
In file included from onscripter.cpp:24:
ONScripterLabel.h:30:23: error: SDL_image.h: No such file or directory
ONScripterLabel.h:31:21: error: SDL_ttf.h: No such file or directory
ONScripterLabel.h:32:23: error: SDL_mixer.h: No such file or directory
ONScripterLabel.h:37:19: error: smpeg.h: No such file or directory
ONScripterLabel.h:44:31: error: vorbis/vorbisfile.h: No such file or directory
In file included from ScriptParser.h:33,
                 from ONScripterLabel.h:27,
                 from onscripter.cpp:24:
ScriptHandler.h:181: warning: ‘typedef’ was ignored in this declaration
In file included from onscripter.cpp:24:
ONScripterLabel.h:77: error: ‘ogg_int64_t’ does not name a type
ONScripterLabel.h:78: error: ‘ogg_int64_t’ does not name a type
ONScripterLabel.h:79: error: ‘OggVorbis_File’ does not name a type
ONScripterLabel.h:545: error: ISO C++ forbids declaration of ‘TTF_Font’ with no type
ONScripterLabel.h:545: error: expected ‘;’ before ‘*’ token
ONScripterLabel.h:552: error: expected ‘;’ before ‘(’ token
ONScripterLabel.h:628: error: ISO C++ forbids declaration of ‘Mix_Music’ with no type
ONScripterLabel.h:628: error: expected ‘;’ before ‘*’ token
ONScripterLabel.h:637: error: ISO C++ forbids declaration of ‘SMPEG’ with no type
ONScripterLabel.h:637: error: expected ‘;’ before ‘*’ token
ONScripterLabel.h:643: error: ISO C++ forbids declaration of ‘Mix_Music’ with no type
ONScripterLabel.h:643: error: expected ‘;’ before ‘*’ token
ONScripterLabel.h:646: error: ISO C++ forbids declaration of ‘Mix_Chunk’ with no type
ONScripterLabel.h:646: error: expected ‘;’ before ‘*’ token
ONScripterLabel.h:653: error: ‘Mix_Chunk’ has not been declared
ONScripterLabel.h:673: error: ISO C++ forbids declaration of ‘TTF_Font’ with no type
ONScripterLabel.h:673: error: expected ‘;’ before ‘*’ token
make: *** [onscripter.o] Error 1

```Help, anyone?

---

### Post by personjerry on 2009-11-29
heh if you're still here, try:

```
sudo apt-get install libvorbis-dev
```

---


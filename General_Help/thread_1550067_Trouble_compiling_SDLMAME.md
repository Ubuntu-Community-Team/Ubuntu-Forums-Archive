---
title: "Trouble compiling SDLMAME"
date: 2010-08-10
forum: General Help
---

### Post by Ember7 on 2010-08-10
I'm running ubuntu 9.10 for powerpc on an ibook G4, and I'm trying to install a program called [SDLMAME]("http://sdlmame.wallyweek.org/") on it.

I assumed because I'm running it on powerpc that I have to compile it myself. So I downloaded the 9.10 version of it, put it in usr/local/src and extracted it. It extracted to a seperate folder named debian, I'm not sure if thats correct or not. I've also installed the libraries stated [here]("http://www.bannister.org/forums/ubbthreads.php?ubb=showflat&Number=35138") :
```
sudo apt-get install build-essential libsdl1.2-dev libgtk2.0-dev libxinerama-dev libgconf2-dev
```

when I run cd /usr/local/src and then ./config I get the error "no such file or directory found". When I run make I get the error "no targets specified and no makefile found" I get the same thing when I use /usr/local/src/debian or paste the files from debian into src.

Is there anything I'm doing wrong?

---


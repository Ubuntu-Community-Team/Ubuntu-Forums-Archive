---
title: "What the heck is this directory?"
date: 2009-11-20
forum: General Help
---

### Post by Snowyfox12 on 2009-11-20
S[FONT=Comic Sans MS]o I was compiling this game from the svn

It's called Super Mario War.  One person said I Had to do some steps however he said 

[/FONT]> change directory into the folder (should be called smw) and configure, make, and make install:
```
./configure
make
sudo make install
```[]("http://forum.72dpiarmy.com/viewtopic.php?f=1&p=190812#")


 I don't understand this.
It maybe for Arch Linux because it's what he's using. I Looked at the svn and there were Debian packages as well. but somebody FIX this. 

JUST FIX THIS AND PUT IT IN CODE TAGS!

---

### Post by lisati on 2009-11-20
You would need to do that from the command line, which, in Ubuntu, is found by opening Applications->Accessories->Terminal menu.

---

### Post by Snowyfox12 on 2009-11-20
All I get is. 
> silveroo@ubuntu:~$ ./configure
bash: ./configure: No such file or directory
silveroo@ubuntu:~$ make
make: *** No targets specified and no makefile found.  Stop.
silveroo@ubuntu:~$ sudo make install
[sudo] password for silveroo: 
make: *** No rule to make target `install'.  Stop.
silveroo@ubuntu:~$ 


---

### Post by BenAshton24 on 2009-11-20
If there are deb packages then just install them instead :P If you want to compile it yourself, all you have to do is go into the main directory (smw) after checking out a revision and follow that guy's instructions.. use the terminal, accessible via Applications -> Accessories -> Terminal

Good Luck..
Ben.

---

### Post by BenAshton24 on 2009-11-20
> **Snowyfox12 said:**
> All I get is.

you are in your home dir there... you need to type
```
cd smw
```
or whatever the directory is called... have a look in nautilus if you are unsure...

EDIT: If you did it via svn then there might be more subdirs before you get to the correct dir, most notably "trunk" , so just experiment a bit...

---

### Post by Snowyfox12 on 2009-11-20
thanks. but... silveroo@ubuntu:~/smw$ ./configure
./configure: 55: sdl-config: not found
./configure: 55: sdl-config: not found
rm -rf build/*
rm -f smw
rm -f leveledit
rm -f worldedit
rm -f smw.exe
rm -f leveledit.exe
rm -f worldedit.exe
rm -f options.bin
rm -rf 'Super Mario War.app'
silveroo@ubuntu:~/smw$ make
g++  -DLINUXFUNC -DPREFIXPATH=\"/usr/share/games/smw\"  -Wall -I. -DPNG_SAVE_FORMAT -o build/FileIO.o -c _src/FileIO.cpp
make: g++: Command not found
make: *** [build/FileIO.o] Error 127
silveroo@ubuntu:~/smw$ sudo make install
g++  -DLINUXFUNC -DPREFIXPATH=\"/usr/share/games/smw\"  -Wall -I. -DPNG_SAVE_FORMAT -o build/FileIO.o -c _src/FileIO.cpp
make: g++: Command not found
make: *** [build/FileIO.o] Error 127
silveroo@ubuntu:~/smw$ 
silveroo@ubuntu:~/smw$ 
silveroo@ubuntu:~/smw$ ./configure
./configure: 55: sdl-config: not found
./configure: 55: sdl-config: not found
rm -rf build/*
rm -f smw
rm -f leveledit
rm -f worldedit
rm -f smw.exe
rm -f leveledit.exe
rm -f worldedit.exe
rm -f options.bin
rm -rf 'Super Mario War.app'
silveroo@ubuntu:~/smw$ make
g++  -DLINUXFUNC -DPREFIXPATH=\"/usr/share/games/smw\"  -Wall -I. -DPNG_SAVE_FORMAT -o build/FileIO.o -c _src/FileIO.cpp
make: g++: Command not found
make: *** [build/FileIO.o] Error 127
silveroo@ubuntu:~/smw$ sudo make install
g++  -DLINUXFUNC -DPREFIXPATH=\"/usr/share/games/smw\"  -Wall -I. -DPNG_SAVE_FORMAT -o build/FileIO.o -c _src/FileIO.cpp
make: g++: Command not found
make: *** [build/FileIO.o] Error 127
 

<_<'

---

### Post by Ancanus on 2009-11-20
You shouldn't run **make** unless **configure** finishes correctly.

I believe to obtain sdl-config you need to

```
 sudo aptitude install libsdl1.2-dev
```also do

```
sudo aptitude install build-essential
```

---

### Post by Snowyfox12 on 2009-11-20
Unavailable. Also the packages for Debian are pretty outdated >_> they were like when 7.10 was around.

---

### Post by Ancanus on 2009-11-20
> **Snowyfox12 said:**
> Unavailable. Also the packages for Debian are pretty outdated >_> they were like when 7.10 was around.

Are you sure they are unavailable? I just tried them in my machine and they worked.
it's LIBSDL1.2-dev not LIBSDLL.2-dev

You can use TAB for auto-completion.

---

### Post by w1ll1am on 2009-11-20
how do you make a new thread can someone please tell me

---

### Post by efflandt on 2009-11-20
w1ll1am, if you go to any forum there is a button at the top or bottom of the list of posts that says "New Thread".

---


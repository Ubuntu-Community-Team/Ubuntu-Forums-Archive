---
title: "Ubuntu is almost no failure ..."
date: 2010-05-10
forum: General Help
---

### Post by tmp2k on 2010-05-10
At first I fell in love with it, the music player, the interface ... just like OSX but without the Jobs, great.
 
But then I tried to install a package that was not part of ubuntu. 
 
I could not create a directory with write access in ../etc/ where I wanted to install it. After 1 hour of sudo, chmod, sh, ls and a LOT of cd I gave up. I also tried gksudo nautilus ... it.wont.work.
 
./program.install ../etc/directory -> error, directory must be writeable ... BUT IT _IS_ WRITEABLE dammit ... :-(

---

### Post by Old *ix Geek on 2010-05-10
> **tmp2k said:**
> At first I fell in love with it, the music player, the interface ... just like OSX but without the Jobs, great.
 
But then I tried to install a package that was not part of ubuntu. 
 
I could not create a directory with write access in ../etc/ where I wanted to install it. After 1 hour of sudo, chmod, sh, ls and a LOT of cd I gave up. I also tried gksudo nautilus ... it.wont.work.
 
./program.install ../etc/directory -> error, directory must be writeable ... BUT IT _IS_ WRITEABLE dammit ... :-(Well, I don't know what you're doing, but in 25 years of using *nix I have yet to be unable to make a directory writable. :confused:  Are you SURE it really is writable? From the error you're getting it sounds like it isn't. Please post the output of
```
ls -l
```
from the parent directory of the directory you're attempting to install the software in.

Also, please explain what you're trying to install and where it needs to be installed.

---

### Post by Dayofswords on 2010-05-10
nvm, misread, ignore this post

consider this a free bump :P

---

### Post by tmp2k on 2010-05-10
Hi :) Well I was trying to install houdini ... I consider myself a linux noob although I have been trying to use it from time to time during the past 15 years or so ;) But those cryptic commands and manual installation processes have always stopped me.
 
Well...ok I typed in gksudo (what does that mean btw ;) nautilus, navigated to the directory that I created ( /etc\houdini) and checked "allow read/write" for myself ... and then tried to install from my home/user directory with the path pointing to etc/houdini ... maybe the settings for /etc/ override the subdirectory I don't know...
 
I will try ls -l ... I didn't know this command...
 
Well ok ls -l tells me drwxrwxrwx 2 (me) users and the directory is blue on green in color ...
 
 
.... Ok ... little update again ;=) I found it. 
 
I typed sh (what does that mean) ./houdini.install ..(SPACEBAR)/etc/houdini
 
I'm almost there --- where is my .login file? and what is 'source' doing ?

---


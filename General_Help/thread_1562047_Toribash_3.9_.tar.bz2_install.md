---
title: "Toribash 3.9 .tar.bz2 install"
date: 2010-08-27
forum: General Help
---

### Post by D4Y.V on 2010-08-27
[http://forum.toribash.com/showpost.php?p=3326798&postcount=45](http://forum.toribash.com/showpost.php?p=3326798&postcount=45)
I've been trying to do everything from what it says on the site to about 10 different tutorials on how to work source code and tar.bz2 and such. Nothing's worked.
absolutely any help is appreciated.
I'm running 9.10 ubuntu.

---

### Post by D4Y.V on 2010-08-27
Wont anyone help? I'm really stuck here.

---

### Post by D4Y.V on 2010-08-27
Still need help!

---

### Post by D4Y.V on 2010-08-27
C'mon there has to be someone.

---

### Post by D4Y.V on 2010-08-27
*Waits for any amount of help.*

---

### Post by D4Y.V on 2010-08-27
Bump.

---

### Post by D4Y.V on 2010-08-27
I have managed to extract the file into "usr/src/toribash_linux-3.9/" but what now? It can't run, I've tried launching the executable "toribash" in said file, I've tried running it as root, but nothing is happening. Is there any help at all?

---

### Post by dragos240 on 2010-08-27
> **D4Y.V said:**
> I have managed to extract the file into "usr/src/toribash_linux-3.9/" but what now? It can't run, I've tried launching the executable "toribash" in said file, I've tried running it as root, but nothing is happening. Is there any help at all?

What about running it in a terminal? If you get errors, post the output.

---

### Post by AlphaLexman on 2010-08-27
ONE bump per day is plenty. People who can help get turned off by users who 'multi-bump' and act impatient.

---

### Post by dragos240 on 2010-08-27
I'm playing it right now. Do this:

sudo apt-get install freeglut3 libguichan-0.8.1-1

I didn't know they had updated toribash for linux, last time I checked it was 3.5

---

### Post by D4Y.V on 2010-08-27
> dave@dave-desktop:~$ /usr/src/toribash_linux-3.9/toribash
/usr/src/toribash_linux-3.9/toribash: error while loading shared libraries: libSDL_mixer-1.2.so.0: cannot open shared object file: No such file or directorySorry, I'm kinda OCD, I think if it goes of the first page i'll never find it again.

EDIT: I tried installing that thing in the console, that didn't work either. I still get this error message.

---

### Post by dragos240 on 2010-08-27
Looks like even SDL isn't installed. Man ubuntu has basic packages.

Try installing this:

sudo apt-get install libsdl-image1.2

---

### Post by D4Y.V on 2010-08-27
I installed it but I still get the same error in the console.

---

### Post by dragos240 on 2010-08-27
I don't use ubuntu. But try this:

sudo apt-get install apt-file

After it finishes, run sudo apt-file update && apt-file search libSDL_mixer-1.2.so.0

---

### Post by D4Y.V on 2010-08-27
```
dave@dave-desktop:~$ apt-file search libSDL_mixer-1.2.so.0
libsdl-mixer1.2: /usr/lib/libSDL_mixer-1.2.so.0
libsdl-mixer1.2: /usr/lib/libSDL_mixer-1.2.so.0.2.6
dave@dave-desktop:~$ /usr/src/toribash_linux-3.9/toribash
/usr/src/toribash_linux-3.9/toribash: error while loading shared libraries: libSDL_mixer-1.2.so.0: cannot open shared object file: No such file or directory
```I did everything you said, and the error still persists.
Also, I'm loving the NGE avi.

---

### Post by D4Y.V on 2010-08-28
1 a day bump

---

### Post by D4Y.V on 2010-08-29
A bump a day keeps the helpers at bay.

---

### Post by D4Y.V on 2010-08-31
Bumple

---

### Post by kakila on 2010-12-08
Hi,
I cannot install toribash 3.9 either.
Under wine I cannot make it work.

However, if you get the fix for the client you will be able to play multiplayer even using the old toribash (that you get with wget as explained in the download page of the official site)

The fix to the client is here
[http://jalis.muistivuoto.net/files/tb_linux-i386_fix.tar.bz2](http://jalis.muistivuoto.net/files/tb_linux-i386_fix.tar.bz2)

Just extract the file and copy it to the place where toribash is installed, in my case /usr/shared/games/toribash

Then you have to go to that flder nad run ./toribash

It should work OK

---


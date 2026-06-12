---
title: "Pioneer Space Sim"
date: 2011-08-02
forum: General Help
---

### Post by Foxcow on 2011-08-02
Has anyone installed this?  Its a remake of the very popular Elite game series and looks really promising. 

[http://pioneerspacesim.net/](http://pioneerspacesim.net/)


The issue I run into is that for the Linux version, there are no installation instructions.  On the download page, there are a few packages that are mentioned (which I have installed) but I'm still getting an error:

```
./pioneer: error while loading shared libraries: libGLEW.so.1.5: cannot open shared object file: No such file or directory
```

I've tried searching for info on this library but can't seem to find anything relevant to Ubuntu or even the package itself.  Does anyone have any idea?  I'm thinking its something ultra-obvious that I'm missing.

---

### Post by Foxcow on 2011-08-02
BUMP

Does anyone know how to get libGLEW.so.1.5 installed and working?

---

### Post by oldos2er on 2011-08-03
[http://pioneerspacesim.net/download](http://pioneerspacesim.net/download) says to run ```
sudo apt-get install libsdl-image1.2 libfreetype6 libsigc++-2.0-0c2a libglew1.5 zlib1g libvorbisfile3 libasound2
```
Have you done that?

---

### Post by Foxcow on 2011-08-03
> **oldos2er said:**
> [http://pioneerspacesim.net/download](http://pioneerspacesim.net/download) says to run ```
sudo apt-get install libsdl-image1.2 libfreetype6 libsigc++-2.0-0c2a libglew1.5 zlib1g libvorbisfile3 libasound2
```
Have you done that?



Yep.  That was the first thing I tired and I already have all of the newest version of each package.  I'm not sure where to go from here.  Google-ing the library doesn't yield anything either.

---

### Post by Foxcow on 2011-08-17
update:

I was able to get that first library,libGLEW.so.1.5, by using getlibs:

```
getlibs -l libGLEW.so.1.5
```

I thought that would solve the issue but now Pioneer requires libstdc++.so.6. I use getlibs to install the i386 version of the library.  The library shows up in the appropriate directory but Pioneer acts like libstdc++.so.6 isn't there and asks for it again.

```
./pioneer: /usr/lib32/libstdc++.so.6: version `GLIBCXX_3.4.15' not found (required by ./pioneer)
```


Any ideas?  I promise to write the entire procedure up once I figure this out.

---

### Post by IanW on 2011-08-17
Alternatively, just run:-

```
sudo apt-get install oolite oolite-data
```

This won't give you Pioneer, but it will give you an actual port of Elite itself.

---

### Post by Foxcow on 2011-08-17
Thanks, I've tried Oolite but would like to get Pioneer running correctly.

---

### Post by racetrack on 2011-08-18
Hi, I'm Rob N, a developer and current release manager for Pioneer.

I'm not a Ubuntu user so i might not know the exact reason for the problem you're experiencing. By the looks of it it seems that you're on a 64-bit system. The binary builds of Pioneer (alphas and nightlies) are 32-bit so you'll need appropriate compatibility libraries.

I can't see if Ubuntu includes a 32-bit compatibility package for libglew - someone here would know better than I. That's what you're aiming for though.

The other option is to build Pioneer from source. Its fairly straightforward; instructions are here:

[http://pioneerspacesim.net/wiki/index.php?title=Compiling_pioneer](http://pioneerspacesim.net/wiki/index.php?title=Compiling_pioneer)

I've heard several reports of success on 64-bit Ubuntu systems, so you shouldn't have too many problems.

There's also a debian/ directory if you feel like building a proper package.

---

### Post by Foxcow on 2011-08-18
> **racetrack said:**
> Hi, I'm Rob N, a developer and current release manager for Pioneer.

I'm not a Ubuntu user so i might not know the exact reason for the problem you're experiencing. By the looks of it it seems that you're on a 64-bit system. The binary builds of Pioneer (alphas and nightlies) are 32-bit so you'll need appropriate compatibility libraries.

I can't see if Ubuntu includes a 32-bit compatibility package for libglew - someone here would know better than I. That's what you're aiming for though.

The other option is to build Pioneer from source. Its fairly straightforward; instructions are here:

[http://pioneerspacesim.net/wiki/index.php?title=Compiling_pioneer](http://pioneerspacesim.net/wiki/index.php?title=Compiling_pioneer)

I've heard several reports of success on 64-bit Ubuntu systems, so you shouldn't have too many problems.

There's also a debian/ directory if you feel like building a proper package.



Hello Rob,

Thanks for your response.  I am in the process of compiling right now.  Thanks for your hardwork as Pioneer looks great.

---

### Post by Foxcow on 2011-08-18
Success!  I compiled using racetrack's instructions and it runs.


My only note on the compilation instructions is to move into the freshly downloaded directory before running 'git checkout alpha13.'  I wouldn't call myself an advanced user but to a total Linux newcomer, it may not be obvious.


Thread marked as solved

---


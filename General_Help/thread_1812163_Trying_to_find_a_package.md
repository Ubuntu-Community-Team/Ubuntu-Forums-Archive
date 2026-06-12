---
title: "Trying to find a package"
date: 2011-07-25
forum: General Help
---

### Post by Scooter_X on 2011-07-25
Hey, so I am trying to install AlephOne so I can play Marathon. I hear it's pretty cool. Anyways, I have to compile it from source, which for some reason I have never been able to compile ANYTHING from source due to dependency issues. 

```
checking for sdl-config... no
checking for SDL - version >= 1.2.0... no
*** The sdl-config script installed by SDL could not be found
*** If SDL was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the SDL_CONFIG environment variable to the
*** full path to sdl-config.
configure: error: You need SDL 1.2 to run Aleph One.

```

This is the specific one I have for what I'm trying to do.

2 questions then: 
-Where can I find this sdl-config package, and
-How in the heck does anyone even know where to look for this stuff in the first place? I went to packages.ubuntu.com and I went to the synaptic package manager, and neither come up with what I need. There is SDL related stuff, but not what I specifically am after. 

Any help appreciated. Thanks.


Oh, BTW I'm running Mint 11.

---

### Post by hyfanious on 2011-07-25
hi
as I concerned sdl-config is not a package, instead its a configuration file for sdl
and also I think u can have access it and edit it after installing this package:
:
'sdl-config' from package 'libsdl1.2-dev'

---

### Post by Scooter_X on 2011-07-26
Oh cool. That got me a step further. How did you know that? Experience I guess? 


Anyway, I installed and now got this: 
```
checking for sdl-config... /usr/bin/sdl-config
checking for SDL - version >= 1.2.0... yes
checking SDL_image.h usability... no
checking SDL_image.h presence... no
checking for SDL_image.h... no
checking SDL_ttf.h usability... no
checking SDL_ttf.h presence... no
checking for SDL_ttf.h... no
checking SDL_net.h usability... no
checking SDL_net.h presence... no
checking for SDL_net.h... no
configure: error: You need SDL_net to run Aleph One.

```

so how am I supposed to get SDL_net now? I assume part of another package?

---

### Post by hyfanious on 2011-07-26
make sure that u have C++ and gcc on ur system
as I see u need them to compile ur file
just use this:
```


sudo apt-get install cpp gcc



```

let me know about ur new results ;)

---

### Post by Scooter_X on 2011-07-26
It says that both of them are already the newest version.

---

### Post by hyfanious on 2011-07-26
use this code to ensure ur file is available or not:

```

locate SDL_image.h


```

or 

```

sudo locate SDL_image.h


```

---

### Post by Scooter_X on 2011-07-26
I tried both. Nothing was returned.

---

### Post by hyfanious on 2011-07-26
so try this code:
```

sudo apt-get install libsdl-image1.2 libsdl-image1.2-dev


```

---

### Post by hyfanious on 2011-07-26
please use this instead:

```

apt-get install libsdl1.2-dev libsdl-image1.2-dev libsdl-mixer1.2-dev libsdl-net1.2-dev gettext libfreetype6-dev automake1.9 g++


```
after that do restart ur machine

with this code u must get all of u need (probably) ;)

---

### Post by Scooter_X on 2011-07-26
```
libsdl-image1.2 is already the newest version.
The following extra packages will be installed:
  libjpeg62-dev libtiff4-dev libtiffxx0c2
The following NEW packages will be installed:
  libjpeg62-dev libsdl-image1.2-dev libtiff4-dev libtiffxx0c2

```

Still doesn't locate SDL_image.h, and stuck at the same spot as before.


OH WAIT- I'LL RESTART! Then I'll let you know.

---

### Post by Scooter_X on 2011-07-26
Closer!!

```
checking for ZZIP... configure: error: Package requirements (zziplib >= 0.10.75) were not met:

No package 'zziplib' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables ZZIP_CFLAGS
and ZZIP_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

---

### Post by hyfanious on 2011-07-26
now use this:
```

sudo apt-get install libzzip-0-13 zziplib-bin libzip-dev 


```

---

### Post by Scooter_X on 2011-07-26
Nothing. Same error.

---

### Post by hyfanious on 2011-07-26
check this page:

[http://sourceforge.net/projects/zziplib/](http://sourceforge.net/projects/zziplib/)

---

### Post by Scooter_X on 2011-07-26
Will do. I'll try whatever I can figure out from there and see what happens tomorrow. It's late where I'm at. Thanks for your help.

---

### Post by oldos2er on 2011-07-26
```
apt-cache search zziplib dev
``` shows ```
libzzip-dev - library providing read access on ZIP-archives - development
``` so I'd install that package if you haven't already.

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

---

### Post by Scooter_X on 2011-07-26
Well, I went to the suggested website, downloaded and compiled the latest package that they had. It worked. I think it's a little frustrating that in the terminal it says 'you need zziplib' but that the package is called 'libzzip'. Almost like I need to be lysdexic to be able to know what to search for in the package manager. :P

Well, I got it, there was another one called 'boost' that I needed, so I installed what was most relevant in the package manager and got it compiled. Thanks for your help.

---


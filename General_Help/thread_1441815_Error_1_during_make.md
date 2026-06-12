---
title: "Error 1 during make"
date: 2010-03-29
forum: General Help
---

### Post by NCLI on 2010-03-29
What went wrong here?

```
install -m 644 /home/seph/kovensky/build/ffmpeg/ffpresets/libx264-baseline.ffpreset /home/seph/kovensky/build/ffmpeg/ffpresets/libx264-default.ffpreset /home/seph/kovensky/build/ffmpeg/ffpresets/libx264-faster.ffpreset /home/seph/kovensky/build/ffmpeg/ffpresets/libx264-faster_firstpass.ffpreset /home/seph/kovensky/build/ffmpeg/ffpresets/libx264-fast.ffpreset /home/seph/kovensky/build/ffmpeg/ffpresets/libx264-fast_firstpass.ffpreset /home/seph/kovensky/build/ffmpeg/ffpresets/libx264-fastfirstpass.ffpreset /home/seph/kovensky/build/ffmpeg/ffpresets/libx264-hq.ffpreset /home/seph/kovensky/build/ffmpeg/ffpresets/libx264-ipod320.ffpreset /home/seph/kovensky/build/ffmpeg/ffpresets/libx264-ipod640.ffpreset /home/seph/kovensky/build/ffmpeg/ffpresets/libx264-lossless_fast.ffpreset /home/seph/kovensky/build/ffmpeg/ffpresets/libx264-lossless_max.ffpreset /home/seph/kovensky/build/ffmpeg/ffpresets/libx264-lossless_medium.ffpreset /home/seph/kovensky/build/ffmpeg/ffpresets/libx264-lossless_slower.ffpreset /home/seph/kovensky/build/ffmpeg/ffpresets/libx264-lossless_slow.ffpreset /home/seph/kovensky/build/ffmpeg/ffpresets/libx264-lossless_ultrafast.ffpreset /home/seph/kovensky/build/ffmpeg/ffpresets/libx264-main.ffpreset /home/seph/kovensky/build/ffmpeg/ffpresets/libx264-max.ffpreset /home/seph/kovensky/build/ffmpeg/ffpresets/libx264-medium.ffpreset /home/seph/kovensky/build/ffmpeg/ffpresets/libx264-medium_firstpass.ffpreset /home/seph/kovensky/build/ffmpeg/ffpresets/libx264-normal.ffpreset /home/seph/kovensky/build/ffmpeg/ffpresets/libx264-placebo.ffpreset /home/seph/kovensky/build/ffmpeg/ffpresets/libx264-placebo_firstpass.ffpreset /home/seph/kovensky/build/ffmpeg/ffpresets/libx264-slower.ffpreset /home/seph/kovensky/build/ffmpeg/ffpresets/libx264-slower_firstpass.ffpreset /home/seph/kovensky/build/ffmpeg/ffpresets/libx264-slow.ffpreset /home/seph/kovensky/build/ffmpeg/ffpresets/libx264-slow_firstpass.ffpreset /home/seph/kovensky/build/ffmpeg/ffpresets/libx264-slowfirstpass.ffpreset /home/seph/kovensky/build/ffmpeg/ffpresets/libx264-ultrafast.ffpreset /home/seph/kovensky/build/ffmpeg/ffpresets/libx264-ultrafast_firstpass.ffpreset /home/seph/kovensky/build/ffmpeg/ffpresets/libx264-veryfast.ffpreset /home/seph/kovensky/build/ffmpeg/ffpresets/libx264-veryfast_firstpass.ffpreset /home/seph/kovensky/build/ffmpeg/ffpresets/libx264-veryslow.ffpreset /home/seph/kovensky/build/ffmpeg/ffpresets/libx264-veryslow_firstpass.ffpreset "/home/seph/kovensky/build/build_libs/share/ffmpeg"
make[1]: Leaving directory `/home/seph/kovensky/build/ffmpeg_build'
script/libass-config
Running autoreconf...
./autogen.sh: 3: autoreconf: not found
Running configure...
./autogen.sh: 5: ./configure: not found
Traceback (most recent call last):
  File "script/libass-config", line 20, in <module>
    main()
  File "script/libass-config", line 18, in main
    check_call(['sh', executable] + args + extra_args)
  File "/usr/lib/python2.6/subprocess.py", line 498, in check_call
    raise CalledProcessError(retcode, cmd)
subprocess.CalledProcessError: Command '['sh', './autogen.sh', '--prefix=/home/seph/kovensky/build/build_libs', '--enable-static', '--disable-shared']' returned non-zero exit status 127
make: *** [libass-config] Error 1

```
I'm trying to [compile Kovensky's mplayer]("http://kovensky.project357.com/sources/") on a 64-bit Ubuntu server.

---

### Post by FakeOutdoorsman on 2010-03-29
Does it require *autoconf*? You could go into the *#mplayer* IRC channel and ask him there.

---

### Post by blazemore on 2010-03-29
You need to [install autoconf]("apt:autoconf").
Click that link if you're in Firefox.

---

### Post by NCLI on 2010-03-30
Done, but now I get a new error(Yay!)

```

make[1]: Leaving directory `/home/seph/kovensky/build/ffmpeg_build'
script/libass-config
Running autoreconf...
Can't exec "libtoolize": No such file or directory at /usr/bin/autoreconf line 189.

```

---

### Post by blazemore on 2010-03-30
> **NCLI said:**
> Done, but now I get a new error(Yay!)

```
make[1]: Leaving directory `/home/seph/kovensky/build/ffmpeg_build'
script/libass-config
Running autoreconf...
Can't exec "libtoolize": No such file or directory at /usr/bin/autoreconf line 189.

```

Here the problem. It's trying to run "libtoolize" but can't.
Let's try and run it ourselves:
```
james@james-desktop:~$ libtoolize
The program 'libtoolize' is currently not installed.  You can install it by typing:
sudo apt-get install libtool
```

So, install libtool.
Rinse and repeat for every other error.
Have fun!

---

### Post by NCLI on 2010-03-30
I figured that out myself actually, but now I have a new new error, and I am stumped -_- It doesn't look like it's a missing package this time.

```
seph/kovensky/build/build_libs/include   -c -o libmpcodecs/vf_softpulldown.o -MD -MP -MF libmpcodecs/vf_softpulldown.d libmpcodecs/vf_softpulldown.c
cc -Wmissing-prototypes -Wundef -Wdisabled-optimization -Wno-pointer-sign -std=gnu99 -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O2 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE64_SOURCE -Ilibdvdread4 -I.  -I/home/seph/kovensky/build/build_libs/include -D_REENTRANT -I/usr/include/directfb -I/usr/include/     -D_REENTRANT    -I/usr/include/freetype2   -I/home/seph/kovensky/build/build_libs/include -I/usr/include/freetype2      -I/home/seph/kovensky/build/build_libs/include   -I/home/seph/kovensky/build/build_libs/include   -I/home/seph/kovensky/build/build_libs/include   -I/home/seph/kovensky/build/build_libs/include   -I/home/seph/kovensky/build/build_libs/include   -c -o libmpcodecs/vf_softskip.o -MD -MP -MF libmpcodecs/vf_softskip.d libmpcodecs/vf_softskip.c
cc -Wmissing-prototypes -Wundef -Wdisabled-optimization -Wno-pointer-sign -std=gnu99 -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O2 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE64_SOURCE -Ilibdvdread4 -I.  -I/home/seph/kovensky/build/build_libs/include -D_REENTRANT -I/usr/include/directfb -I/usr/include/     -D_REENTRANT    -I/usr/include/freetype2   -I/home/seph/kovensky/build/build_libs/include -I/usr/include/freetype2      -I/home/seph/kovensky/build/build_libs/include   -I/home/seph/kovensky/build/build_libs/include   -I/home/seph/kovensky/build/build_libs/include   -I/home/seph/kovensky/build/build_libs/include   -I/home/seph/kovensky/build/build_libs/include   -c -o libmpcodecs/vf_swapuv.o -MD -MP -MF libmpcodecs/vf_swapuv.d libmpcodecs/vf_swapuv.c
cc -Wmissing-prototypes -Wundef -Wdisabled-optimization -Wno-pointer-sign -std=gnu99 -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O2 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE64_SOURCE -Ilibdvdread4 -I.  -I/home/seph/kovensky/build/build_libs/include -D_REENTRANT -I/usr/include/directfb -I/usr/include/     -D_REENTRANT    -I/usr/include/freetype2   -I/home/seph/kovensky/build/build_libs/include -I/usr/include/freetype2      -I/home/seph/kovensky/build/build_libs/include   -I/home/seph/kovensky/build/build_libs/include   -I/home/seph/kovensky/build/build_libs/include   -I/home/seph/kovensky/build/build_libs/include   -I/home/seph/kovensky/build/build_libs/include   -c -o libmpcodecs/vf_tcdump.o -MD -MP -MF libmpcodecs/vf_tcdump.d libmpcodecs/vf_tcdump.c
libmpcodecs/vf_tcdump.c:9:21: error: help_mp.h: No such file or directory
libmpcodecs/vf_tcdump.c: In function 'put_image':
libmpcodecs/vf_tcdump.c:51: error: 'MSGTR_MPCODECS_TCDumpNoPTS' undeclared (first use in this function)
libmpcodecs/vf_tcdump.c:51: error: (Each undeclared identifier is reported only once
libmpcodecs/vf_tcdump.c:51: error: for each function it appears in.)
libmpcodecs/vf_tcdump.c:57: error: 'MSGTR_MPCODECS_TCDumpOpenFail' undeclared (first use in this function)
make[1]: *** [libmpcodecs/vf_tcdump.o] Error 1
make[1]: Leaving directory `/home/seph/kovensky'
make: *** [mplayer] Error 2

```

---

### Post by NCLI on 2010-03-31
It turns out the git was broken. fixed now, and everything is working, so I'm marking this one as solved.

---


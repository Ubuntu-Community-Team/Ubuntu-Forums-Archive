---
title: "libjpeg.so.62 =&gt; not found"
date: 2012-10-07
forum: General Help
---

### Post by madinc on 2012-10-07
trying to play a game on amd64 12.04 and keep getting this error.



```
using ARB_vertex_buffer_object memory
using ARB2 renderSystem
found DLL in pak file: /home/madinc/.doom3/darkmod/tdm_game02.pk4/gamex86.so
copy gamex86.so to /home/madinc/.doom3/darkmod/gamex86.so
dlopen '/home/madinc/.doom3/darkmod/gamex86.so' failed: libjpeg.so.62: cannot open shared object file: No such file or directory
Regenerated world, staticAllocCount = 0.
Shutting down sound hardware
----------- Alsa Shutdown ------------
close pcm
dlclose
--------------------------------------
idRenderSystem::Shutdown()
Sys_Error: couldn't load game dynamic library

```and this

```
madinc@Madinc-1:~/.doom3/darkmod$ ldd gamex86.so
    linux-gate.so.1 =>  (0xf778b000)
    librt.so.1 => /lib/i386-linux-gnu/librt.so.1 (0xf6a84000)
    libjpeg.so.62 => not found
    libpng12.so.0 => /lib/i386-linux-gnu/libpng12.so.0 (0xf6a59000)
    libstdc++.so.6 => /usr/lib/i386-linux-gnu/libstdc++.so.6 (0xf6974000)
    libm.so.6 => /lib/i386-linux-gnu/libm.so.6 (0xf6948000)
    libgcc_s.so.1 => /lib/i386-linux-gnu/libgcc_s.so.1 (0xf692a000)
    libc.so.6 => /lib/i386-linux-gnu/libc.so.6 (0xf6780000)
    libpthread.so.0 => /lib/i386-linux-gnu/libpthread.so.0 (0xf6764000)
    libz.so.1 => /lib/i386-linux-gnu/libz.so.1 (0xf674e000)
    /lib/ld-linux.so.2 (0xf778c000)

```but i have this lib installed 

```
madinc@Madinc-1:~$ locate libjpeg
/home/madinc/Amnesia/libs64/libjpeg.so.62
/home/madinc/ETQW/libjpeg.so.62
/home/madinc/Mad-Projects/etqw_1.5_all/usr/share/games/etqw/libjpeg.so.62
/usr/lib/darktable/plugins/imageio/format/libjpeg.so
/usr/lib/games/zero-ballistics/shared_libs/libjpeg.so.62
/usr/lib/i386-linux-gnu/libjpeg.so.8
/usr/lib/i386-linux-gnu/libjpeg.so.8.0.2
/usr/lib/jvm/java-6-openjdk-amd64/jre/lib/amd64/libjpeg.so
/usr/lib/x86_64-linux-gnu/libjpeg.so.62
/usr/lib/x86_64-linux-gnu/libjpeg.so.62.0.0
/usr/lib/x86_64-linux-gnu/libjpeg.so.8
/usr/lib/x86_64-linux-gnu/libjpeg.so.8.0.2

```reinstall makes no difference any ideas guys?

---

### Post by dodo3773 on 2012-10-07
Just a shot in the dark here but are you sure it is installed? Looking at the output there this looks like a multilib system and the game you are trying to play is looking in "/lib/i386-linux-gnu/" instead of "/usr/lib/x86_64-linux-gnu/". I am assuming that this is because the game you are trying to play needs 32 bit libs instead of the 64 bit ones. Search in your package manager for libjpeg and see if there is a multilib version or a 32 bit lib available.

---

### Post by madinc on 2012-10-07
> **dodo3773 said:**
> Just a shot in the dark here but are you sure it is installed? Looking at the output there this looks like a multilib system and the game you are trying to play is looking in "/lib/i386-linux-gnu/" instead of "/usr/lib/x86_64-linux-gnu/". I am assuming that this is because the game you are trying to play needs 32 bit libs instead of the 64 bit ones. Search in your package manager for libjpeg and see if there is a multilib version or a 32 bit lib available.


sorry for the late reply but i was enjoying the game :lolflag: i found a solution to my problem in launchpad i think this is some kind of bug [https://bugs.launchpad.net/ubuntu/+source/libjpeg6b/+bug/978843](https://bugs.launchpad.net/ubuntu/+source/libjpeg6b/+bug/978843)

apparently there is many people with this problem but one of them had a solution that worked for me.

> [limaxray (matt-limaxray)]("https://launchpad.net/%7Ematt-limaxray")             wrote             on 2012-05-03:                                                            [ #11]("https://bugs.launchpad.net/ubuntu/+source/libjpeg6b/+bug/978843/comments/11")                                                               I have the same  problem on a x86_64 Precise install - unable to run Cadsoft Eagle due to  libjpeg.so.62 not being found.  I can confirm the libjpeg62 package is  installed through apt, but only the x86_64 libraries were installed.
 I was able to workaround the problem my manually downloading and installing the i386 package from here:
 [http://packages.ubuntu.com/precise/i386/libjpeg62/download](http://packages.ubuntu.com/precise/i386/libjpeg62/download)

              
so i downloaded the deb here [http://packages.ubuntu.com/precise/i386/libjpeg62/download](http://packages.ubuntu.com/precise/i386/libjpeg62/download)

and reinstall the package with gdebi for some odd reason only the x86_64 libraries were installed.:mad:

anyway its all good now thank you for the reply.

---


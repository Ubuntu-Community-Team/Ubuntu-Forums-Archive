---
title: "Crash in sdl/libpng/libc/?, &quot;missing memcpy-ssse3.S&quot;"
date: 2010-10-24
forum: General Help
---

### Post by iliis on 2010-10-24
Hello

Sauerbraten (FPS: [http://sauerbraten.org/](http://sauerbraten.org/)), SMC (Jump'n'Run: [http://www.secretmaryo.org/](http://www.secretmaryo.org/)) and Wesnoth (RTS: [http://www.wesnoth.org/](http://www.wesnoth.org/)) all crash at startup while loading some images.

gdb backtraces:

**sauerbraten:**
[http://pastebin.com/SSb9iZKR](http://pastebin.com/SSb9iZKR)
[http://pastebin.com/PiwBk2iC](http://pastebin.com/PiwBk2iC)
[http://pastebin.com/jdK4SXMR](http://pastebin.com/jdK4SXMR)
they are all almost the same, apart from trying to load different images. I tried it multiple times, with seemingly random results.
Version: sauerbraten-dbg from multiverse repositories. (0.0.20100728.dfsg-2)

**secret maryo chronicles:**
[http://pastebin.com/wrJxwVmm](http://pastebin.com/wrJxwVmm)
Version: Also from the repos, but the normal version (as I couldn't find a debug version and didn't want to compile one): Version: 1.9-3 (from universe)
[B]
Battle for Wesnoth:[/B]
[http://pastebin.com/0gB5BKB8](http://pastebin.com/0gB5BKB8)
Version: 1:1.8.5-1 (universe)

These are the games that crash the same way. As these don't have much in common besides using SDL_image, the error seems quite strange and my system is quite an old mess (Ubuntu 10.10 kernel 2.6.35-22-generic
, but started out at 8.04 or even 7.10), I suspect that it's an configuration/installation/whatever-error rather than a bug in sauerbraten/smc/sdl/libpng/libc.

[FONT=Courier New]**aptitude show ...**
libpng12-0: Version: 1.2.44-1
libc6: Version: 2.12.1-0ubuntu8
libsdl-debian: Version: 1.2.14-6ubuntu3
libsdl-image1.2: Version: 1.2.10-2[/FONT]

GPU: NVidia GeForce 8800 GTS 512, drivers 256.53

Compiz is running (1:0.8.6-0ubuntu9.1), but disabling it ([FONT=Courier New]metacity --replace[/FONT]) changes nothing. Other graphics-heavy programs (other games, blender, self-written-sdl-stuff, etc.) show no problems at all.

Any ideas? Where is/should be ../sysdeps/i386/i686/multiarch/memcpy-ssse3.S:399?
Any help would be greatly appreciated ;)
Cheers, iliis

---

### Post by iliis on 2010-11-18
Nobody any idea at all? Well, me neither :/

---


---
title: "Not so typical conky problem..."
date: 2012-08-24
forum: General Help
---

### Post by ihatethisflavorsomuch on 2012-08-24
Okay so I've been reading nonstop about this conky config for two weeks and I'm literally going bonkers over this damn conky config...when I type conky in the terminal this is what I get:


Conky: /home/wayne/.conkyrc: 104: no such configuration: 'imlib_cache_size'
Conky: llua_load: /home/wayne/.conky/draw_bg.lua:71: module 'cairo' not found:
no field package.preload['cairo']
no file './cairo.lua'
no file '/usr/local/share/lua/5.1/cairo.lua'
no file '/usr/local/share/lua/5.1/cairo/init.lua'
no file '/usr/local/lib/lua/5.1/cairo.lua'
no file '/usr/local/lib/lua/5.1/cairo/init.lua'
no file '/usr/share/lua/5.1/cairo.lua'
no file '/usr/share/lua/5.1/cairo/init.lua'
no file '/usr/local/lib/conky/libcairo.so'
no file './cairo.so'
no file '/usr/local/lib/lua/5.1/cairo.so'
no file '/usr/lib/i386-linux-gnu/lua/5.1/cairo.so'
no file '/usr/lib/lua/5.1/cairo.so'
no file '/usr/local/lib/lua/5.1/loadall.so'
Conky: llua_load: /home/wayne/.conky/bargraph_small.lua:158: unexpected symbol near 'if'
Conky: forked to background, pid is 18932

Conky: desktop window (1a00095) is subwindow of root window (b2)
Conky: window type - normal
Conky: drawing to created window (0x1200002)
Conky: drawing to double buffer
Conky: llua_do_call: function conky_draw_bg execution failed: attempt to call a nil value
Conky: llua_do_call: function conky_main_bars execution failed: attempt to call a nil value

(repeated for as long as conky remains open.) conky still works for the most part but it just has been urking me that everyone else has been able to get this working besides myself. The last time I had a conky problem I quit using it for 3 years.

Does anyone have any idea on how I can fix this, so I can stop smashing my head against the wall and ripping my hair out. I don't even have any more keyboards to snap in half over my knee. HELP! PLEASE!

P.S. yes i know I already posted this in a solved topic, lets not be juvenile and point that out, please just help direct me in the proper direction.

P.S.S. I really just want to know if I don't have those files how do I end up installing them. I can figure the conky stuff out on my own. I looked in the software center and nothing, did I just end up screwing up the conky install? Should I uninstall all of this and reinstall?

---

### Post by Habitual on 2012-08-24
terminal > 
```
conky -v
```

Please use the "#" when posting output or requested text/commands/etc :)

---

### Post by ihatethisflavorsomuch on 2012-08-24
> **Habitual said:**
> terminal > 
```
conky -v
```

Please use the "#" when posting output or requested text/commands/etc :)

I dunno what you mean by use the "#"...?:confused:

wayne@wayne-laptop:~$ conky -v
Conky 1.8.1 compiled Mon Oct 17 16:49:09 EDT 2011 for Linux 3.0.0-12-generic-pae (i686)

Compiled in features:

System config file: /usr/local/etc/conky/conky.conf
Package library path: /usr/local/lib/conky

 X11:
  * Xdamage extension
  * XDBE (double buffer extension)
  * Xft
  * ARGB visual

 Music detection:
  * MPD
  * MOC

 General:
  * math
  * hddtemp
  * portmon
  * config-output
  * apcupsd
  * iostats
  * ncurses
  * Lua

  Lua bindings:


I usually don't participate in the forums, I use it as a last resort before I'm pulling my hair out.

---

### Post by Sector11 on 2012-08-24
> **ihatethisflavorsomuch said:**
> I dunno what you mean by use the "#"...?:confused:

```
wayne@wayne-laptop:~$ conky -v
Conky 1.8.1 compiled Mon Oct 17 16:49:09 EDT 2011 for Linux 3.0.0-12-generic-pae (i686)

Compiled in features:

System config file: /usr/local/etc/conky/conky.conf
Package library path: /usr/local/lib/conky

 X11:
  * Xdamage extension
  * XDBE (double buffer extension)
  * Xft
  * ARGB visual

 Music detection:
  * MPD
  * MOC

 General:
  * math
  * hddtemp
  * portmon
  * config-output
  * apcupsd
  * iostats
  * ncurses
  * Lua

  Lua bindings:

```

I usually don't participate in the forums, I use it as a last resort before I'm pulling my hair out.

When editing/creating a post on the menu bar above the text area you see a # - 3rd from the right.  That will put code inside code blocks like I did with your quoted message terminal output.  Easier for people to read.

You are using the standard conky v1.8.1 - it's a bit buggy.  [You can upgrade to conky v1.9.0-2 like this]("http://ubuntuforums.org/showpost.php?p=12065119&postcount=11")

And doesn't have everything you need:
```
  24 Aug 12 | 11:35:49 ~
         $ conky -v
Conky 1.9.0 compiled Fri May 11 15:54:00 UTC 2012 for Linux 2.6.32-5-amd64 (x86_64)

Compiled in features:

System config file: /etc/conky/conky.conf
Package library path: /usr/lib/conky

 X11:
  * Xdamage extension
  * XDBE (double buffer extension)
  * Xft
  * ARGB visual

 Music detection:
  * Audacious
  * MPD
  * MOC
  * XMMS2

 General:
  * math
  * hddtemp
  * portmon
  * Curl
  * RSS
  * Weather (METAR)
  * Weather (XOAP)
  * wireless
  * support for IBM/Lenovo notebooks
  * nvidia
  * eve-online
  * config-output
  * Imlib2
  * apcupsd
  * iostats
  * ncurses
  * Lua

  Lua bindings:
   * Cairo
   * Imlib2

  24 Aug 12 | 11:35:53 ~
         $ 
```

These:
```
  Lua bindings:
   * Cairo
   * Imlib2
```

are a must for the conky you are trying to run.

---


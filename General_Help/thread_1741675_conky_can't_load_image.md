---
title: "conky can't load image"
date: 2011-04-28
forum: General Help
---

### Post by Afsoon on 2011-04-28
Hi people, I have one error with a skin conky. When i execute a conky it display a error 

```
rm: no se puede borrar «/home/said/.tonky/notify/oncal»: No existe el fichero o el directorio
rm: no se puede borrar «/home/said/.tonky/notify/oncpu»: No existe el fichero o el directorio
rm: no se puede borrar «/home/said/.tonky/notify/onmem»: No existe el fichero o el directorio
rm: no se puede borrar «/home/said/.tonky/notify/onwet»: No existe el fichero o el directorio
rm: no se puede borrar «/home/said/.tonky/notify/onwifi»: No existe el fichero o el directorio
Conky: desktop window (1c000ae) is subwindow of root window (b9)
Conky: window type - override
Conky: drawing to created window (0x5a00001)
Conky: drawing to double buffer
Conky: Unable to load image '-s'
Conky: Unable to load image '-s'
Conky: Unable to load image '-s'

```

The README say:
```
you need conky 1.7.1.+ (Configure Conky with the `--enable-imlib2' option)
```
I have conky conky 1.8.0 and install conky-all. I execute conky -v I have a imlib2
```
Conky 1.8.0 compiled Fri Apr 23 10:38:37 UTC 2010 for Linux 2.6.24-27-server (i686)

Compiled in features:

System config file: /etc/conky/conky.conf
Package library path: /usr/lib/conky

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
  * ALSA mixer support
  * apcupsd
  * iostats
  * ncurses
  * Lua

  Lua bindings:
   * Cairo
   * Imlib2
```
I think, that error can be because i have a smaller display. If any can help me to solve that error.

PD: Sorry for my bad English, I study harder English

---

### Post by stinkeye on 2011-05-03
Did you name a folder incorrectly.
```
/home/said/**.tonky**/notify/oncal»
```
Is that supposed to be **.conky** ?

---


---
title: "Conky imlib2 problem"
date: 2009-11-03
forum: General Help
---

### Post by psylightxplosion on 2009-11-03
HI
I've installed ubuntu 9.10 and I  have problem with my conky
I installed it by using apt and it shows imlib2 enabled but it won't show any picture

here is the "conky -v" output
> viper@localhost:~$ conky -v
Conky 1.7.2 compiled Fri Oct 23 15:55:48 UTC 2009 for Linux 2.6.24-23-server (i686)

Compiled in features:

System config file: /etc/conky/conky.conf
Package library path: /usr/lib/conky

 X11:
  * Xdamage extension
  * XDBE (double buffer extension)
  * Xft

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
  * Lua

  Lua bindings:
   * Cairo
   * Imlib2


---

### Post by psylightxplosion on 2009-11-04
Anyone ??

---

### Post by helmuthdu on 2009-12-18
try an apt-get install conky-all :)

---

### Post by substream on 2011-08-31
Odd.. Images worked perfectly for me in Ubuntu, but I just switched to Crunchbang and I'm not having the exact same problem as you. I compiled Conky myself with everything enabled except the plugins for audio programs and confirmed that imlib2 was installed, but my Conky still will not draw images :(

---


---
title: "sudo apt-get install lib32ncurses5-dev ( Unable to locate package lib32ncurses5-dev)"
date: 2011-07-31
forum: General Help
---

### Post by JaizEdelmann on 2011-07-31
Hey I'm trying to install my tvcard ([http://linuxtv.org/wiki/index.php/Technisat_CableStar_HD2](http://linuxtv.org/wiki/index.php/Technisat_CableStar_HD2)) on a freshly installed maverik minimal installation, i had no problem gettin the lib32ncurses5-dev package on lucid, but after i got maverik i cant seem to find it.

Any help would be great :)

Doh never mind, forgot i was on 64bit (sudo apt-get install libncurses5-dev)

---

### Post by galvatron408 on 2011-07-31
sudo apt-cache search libncurses
libncurses5 - shared libraries for terminal handling
libncurses5-dbg - debugging/profiling libraries for ncurses
libncurses5-dev - developer's libraries for ncurses
libncursesw5 - shared libraries for terminal handling (wide character support)
libncursesw5-dbg - debugging/profiling libraries for ncursesw
libncursesw5-dev - developer's libraries for ncursesw
centerim-utf8 - A text-mode multi-protocol instant messenger client
libncurses-gst - Ncurses bindings for GNU Smalltalk
libncurses-ruby - ruby Extension for the ncurses C library
libncurses-ruby1.8 - ruby Extension for the ncurses C library
libncurses-ruby1.9.1 - ruby Extension for the ncurses C library

---


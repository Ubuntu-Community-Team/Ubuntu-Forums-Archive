---
title: "Changes in /usr/share/X11/xkb/symbols/us have no effect"
date: 2012-06-08
forum: General Help
---

### Post by PaalD on 2012-06-08
Hi.

I am using ubuntu 12.04 with fluxbox as my window manager. The last few days I have
been trying to get rid of an annoying dead key behaviour related to the tilde and
apostrophe keys. In particular, I have made the following changes in 
/usr/share/X11/xkb/symbols/us:

OUT:
====
key <TLDE> { [dead_grave, dead_tilde,         grave,       asciitilde ] };
key <AC11> { [dead_acute, dead_diaeresis, apostrophe,        quotedbl ] };

IN:
===
key <TLDE> { [     grave, asciitilde,    dead_grave,       dead_tilde ] };
key <AC11> { [apostrophe,   quotedbl,    dead_acute,    dead_diaeresis] };

The problem is that if I switch back and forth between two different layouts
(for instance 'no' and 'alt-intl') using 'setxkbmap us -variant alt-intl' the changes 
have no effect.

What am I doing wrong?

---

### Post by PaalD on 2012-07-26
It turns out that keymaps are compiled and pre-cached in directory /var/lib/xkb/. These
maps are updated only as needed. Unfortunately, changes made to the underlying 
/usr/share/X11/xkb/symbols/us didn't trigger any updates. At least not with fluxbox. 

Very frustrating.

Removing the cached keymaps solved the matter.

---


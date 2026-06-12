---
title: "Dolphin emulator does not load any games"
date: 2011-01-10
forum: General Help
---

### Post by ShadowWraith on 2011-01-10
I just installed the dolphin gamecube/wii emulator by compiling from svn
as per the instructions here: [http://code.google.com/p/dolphin-emu/wiki/Linux_Build](http://code.google.com/p/dolphin-emu/wiki/Linux_Build)

Everything seems fine, except that when I load any game, the entire emulator simply freezes. This is the only thing resembling an error that
is printed on the command line:

```

(dolphin-emu:19696): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.24.1/gobject/gsignal.c:2390: instance `0x998cbc8' has no handler with id `1821'
Killed

```

Can anyone help?

---

### Post by ShadowWraith on 2011-01-10
Bump. More info: The error message above comes up when the gui is loaded.
There is absolutely no message on the command line when I load any game - the emulator just hangs like it's gone into an infinite loop. I've already compiled  and tried the latest 3 revisions from the svn, and no luck.

---

### Post by ShadowWraith on 2011-01-10
I have narrowed down the problem:

The problem seems to lie in the JIT recompiler. When I set the cpu emulation mode to interpreter the game starts up - albeit very slowly.

Can anyone help?

---

### Post by IzeHouze on 2011-01-12
Used PPA to install onto a 10.10 machine.  It ran fine.  Locked screen, came back today, logged in, it no longer works.  Screen simply fades and does not run.  Confirmed, when JIT is not used games load, slowly.  Un-installed, downloaded source, complied, installed, same issue.  Try to load game with JIT, simply hangs and fades.  No messages from console...

---


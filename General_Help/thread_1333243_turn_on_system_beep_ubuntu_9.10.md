---
title: "turn on system beep ubuntu 9.10"
date: 2009-11-21
forum: General Help
---

### Post by xeemo on 2009-11-21
it seems that the internal system beep is off by default in 9.10 (or at least that's what i'm assuming, because mine isn't on.)  believe it or not i want that turned on.  can anyone help?  thanks.:D

---

### Post by bluplr on 2009-11-21
It could be that your pc speaker module is not loaded, but before trying to fix that try going system>administration>synaptic package manager>search beep> install beep.

If that fails, try opening a terminal and running xset b on

If that doesn't work, try and load your speaker by running in a terminal, sudo modprobe pcspkr

Running echo -e '\a' in the terminal should make the system beep. As should the command, beep. The last 2 methods may reset after reboot, if they fix the problem, post here and I'll tell you how to make them permanent. 

This problem seems to be fairly widespread, see [this](http://ubuntuforums.org/showthread.php?p=8238852) thread for more fixes.

---

### Post by xeemo on 2009-11-21
thanks for the reply. i got it back up and running thanks to the instructions at [http://andrewgee.org/blog/2009/11/14/pc-speaker-karmic/](http://andrewgee.org/blog/2009/11/14/pc-speaker-karmic/) .

---


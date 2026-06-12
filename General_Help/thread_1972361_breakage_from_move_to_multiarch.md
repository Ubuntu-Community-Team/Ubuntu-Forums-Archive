---
title: "breakage from move to multiarch?"
date: 2012-05-03
forum: General Help
---

### Post by mel_yeuxdoux on 2012-05-03
If I understand rightly, 12.04 is the first Ubuntu version to use multiarch. Does that require any change to, for example, 32-bit x86 programs to be run on 64-bit?

I ask because when I upgraded to 12.04, Second Life clients started freezing when I try to save a snapshot to disk, and despite pleas from various users (me included) Linden Lab has yet to put out a real 64-bit client, so it is counting on the ability to run 32-bit programs under 64-bit Linux.

UPDATE: the message shows that it's trying to load a library, but since said library is 64-bit and the SL client is 32-bit, it fails. The message:


2012-05-06T12:13:25Z INFO: beforeDialog: LLWindowSDL::beforeDialog()
/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(do-not-directly-run-secondlife-bin:30585): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

---


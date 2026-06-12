---
title: "Expo Key missing in keyboard shortcuts"
date: 2009-09-23
forum: General Help
---

### Post by linuxcss on 2009-09-23
on 2 systems i have ubuntu installed and even with the same keyboard I find one system shows

in system->perferences->keyboard shortcuts  under desktop section that on one system
I have 4 entries that are not on the other system

Initiate Window Picker
Zoom in
Zoom out
Expo Key

why is this? I miss being able to use the Expo key action ... is there some other setting needed?
also in system->preferences->Keyboard and then in layout section  I see Generic 105-key (Intl) PC
on both systems.

I also did a live boot on system that still does NOT  list the 4 entries 

Is this a bug or does some one know how to fix this  so that the four above missing entries appear and allow the functionality of the Expo key!

I'm using ubuntu 9.04 on both computers

---

### Post by linuxcss on 2009-09-24
bump, thought I hear an answer by now.

---

### Post by wojox on 2009-09-24
I'm running Jaunty and they are all there. What about adding them yourself?

---

### Post by linuxcss on 2009-09-24
How do i Hook this in with 'add' on keyboard shortcuts?

Is it some executable file ?

---

### Post by dowcet on 2010-06-11
Linuxcss, did you ever figure this out? My expo feature suddenly stopped working, and I no longer see "Expo key" under keyboard shortcuts like I once did, even though it is still set correctly in CCSM :(

---

### Post by mbyrd11 on 2010-10-13
I know that by default the expo key is "Super + e" 

But I am having the same issue as you are in that I don't see the expo key in the keyboard shortcuts.


Sorry for bringing back a dead thread (rhyme hehe)

---

### Post by GB_Joe on 2010-12-11
Hmmm. So much for a dead thread!

I've just done a fresh install of 10.10 and there's no Expo option on the Keyboard Shortcuts list. Having poked around a few other threads (specifically [http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1487158]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1487158")) I ended up running gconfig-editor to see what was in there, and it turns out that on my system the Expo section is missing from there too.

Moving on to the next thread: [http://newyork.ubuntuforums.org/showthread.php?t=1587290]("http://newyork.ubuntuforums.org/showthread.php?t=1587290")

It looks like this is an ongoing bug.
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/654063]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/654063")

---

### Post by mauchroucinia on 2011-03-23
go into terminal, and type in:

sudo apt-get install compizconfig-settings-manager xautomation

once that is done go to system>preferences>compizconfig settings manager

search "expo" (no quotations, of course) and from there you can change the keyboard shortcut, among other things

---


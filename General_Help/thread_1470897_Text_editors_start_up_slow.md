---
title: "Text editors start up slow"
date: 2010-05-03
forum: General Help
---

### Post by Zeemvel on 2010-05-03
Hi,

Whenever I start a text editor, such as kate, kwrite, gedit, it takes at least 10 seconds to start up.

This on a PC with 4 cores and 3GB RAM.

I know that these text editors should start up much faster, like, I click the launch icon and it should already by there.

But instead it's 10 seconds waiting and then the editor is there.

Why, what's it doing during those 10 seconds, and most important, how can I fix this?

---

### Post by Vaphell on 2010-05-03
try launching from terminal to see if there are any errors/warnings that could provide some useful info.

---

### Post by Zeemvel on 2010-05-17
> **Vaphell said:**
> try launching from terminal to see if there are any errors/warnings that could provide some useful info.

I tried this in a terminal, to start gedit.

After I type "gedit" and press enter, it just waits 8 seconds, then the gedit window appears.

No messages appear.

I know a 386 computer, 33Mhz, that can start wordpad in a second. So this behaviour is not normal from (K)Ubuntu...

---

### Post by Zorael on 2010-05-17
Try creating a new user and see if it happens when logged in as him/her as well. It could be something like your places bookmarks having links to somewhere the applications can't read, so it's trying for a few seconds before eventually giving up.

The only "real" way I know of to determine what's happening is to install the debugging packages, and then debug the startup process with gdb or valgrind with cachegrind.

---


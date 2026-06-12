---
title: "emacs bug"
date: 2010-10-26
forum: General Help
---

### Post by jbf81tb on 2010-10-26
I'm sorry if this is in the wrong place, I just wanted to get the topic out there to see if anyone knows anything about it. I'm open to any advice as to where to move this question to get better help.

I'm using PuTTY to connect to a server with x11 forwarding. Whenever I try to open emacs in the terminal I get this prompt:


** (emacs:4795): CRITICAL **: murrine_style_draw_box: assertion `height >= -1' failed


It doesn't really affect anything, but it is quite annoying. It's been happening for about a month now, and I've updated since then. 

This is the emacs I'm using:

GNU Emacs 23.1.1 (x86_64-pc-linux-gnu, GTK+ Version 2.20.0)

Thank you to anyone who can provide some help! :-)

---

### Post by ch1ll1man on 2010-10-26
Take a look at the following bug post

[https://bugs.launchpad.net/ubuntu/+source/emacs23/+bug/538541](https://bugs.launchpad.net/ubuntu/+source/emacs23/+bug/538541)

Should answer your question for you.

---


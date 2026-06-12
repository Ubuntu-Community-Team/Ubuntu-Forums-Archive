---
title: "Can't log in"
date: 2010-08-10
forum: General Help
---

### Post by jcaplis on 2010-08-10
So I just installed 10.04 yesterday and everything was working great this morning. However, I booted up this afternoon and when I tried to log in the screen goes black and the mouse tells me it's loading but then I end up back at the log in screen. My password is correct. The only thing that changed from this morning was an update that was installed, but I don't remember what it was. Any thoughts as to why this is happening?

---

### Post by Zorgoth on 2010-08-10
Don't know why it's happening, but try booting up into recovery mode, dropping into a root shell when you have the option, and running the command:

adduser testing.

Then attempt to log in as that user.  This will help determine whether the problem is in your home directory or with the system.

Another thing you can try is to get to the same root shell, and run:

su your_username
startx

See if that gets you in or not.

---

### Post by jcaplis on 2010-08-11
I'm new to Ubuntu. How do I do that?

---

### Post by jcaplis on 2010-08-17
Bump.

---


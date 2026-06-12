---
title: "tclUDP"
date: 2006-05-08
forum: General Help
---

### Post by ok67 on 2006-05-08
I am trying to run a dummy GPS program named gpsfeed+, it is a tcl program. However it needs a package to tcl named tclUDP. It don't look like this is available to Ubuntu, it looks like I have to compile the tclUDP package myselves and probably also tcl....

---

### Post by louis_nichols on 2006-05-08
That may be so. And I'd like to help, but I don't see a question in your post. :)

---

### Post by ok67 on 2006-05-10
Uhm, well the question is do this tclUDP exist as a precompiled installable package to Ubuntu or not? If it does not exist, is there any posibility the it will do so in the nearest furure?

---

### Post by louis_nichols on 2006-05-10
I can't find it in synaptic.

did you try compiling it from source?

---

### Post by ok67 on 2006-05-10
[QUOTE=louis_nichols]I can't find it in synaptic.

did you try compiling it from source?[/QUOTE]
No, but I beleive I have to......
That's no problem, since untill two years ago I was running Slackware.... But I don't like the idea of mixing Ubuntu packages with self compiled software, but if I have to I'll do it.

---

### Post by louis_nichols on 2006-05-10
I completely understand your point of view.

This is why, whenever I compile a package, I install it with checkinstall. It won't be a complete deb package, it will lack any info about deps and stuff, but it's guaranteed to work on your machine, since you compiled, and the great advantage is that it will be easily removed via any of the tools.

---


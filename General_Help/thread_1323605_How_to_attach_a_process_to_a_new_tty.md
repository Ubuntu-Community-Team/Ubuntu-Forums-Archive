---
title: "How to attach a process to a new tty?"
date: 2009-11-11
forum: General Help
---

### Post by ypsd on 2009-11-11
I remotely login from machine B to machine A and I start a process in tty 10 on A.

Then I'm away from machine B and have no access to machine B any more.

I remotely login from machine C to machine A. I see the process is still running (maybe waiting for my input). I'm wondering if it is possible to attach the process to a new tty so that I can control it?

---

### Post by nocnokneo on 2011-07-13
[https://github.com/nelhage/reptyr](https://github.com/nelhage/reptyr)

---

### Post by Lars Noodén on 2011-07-13
If you launched the original process under [screen](https://help.ubuntu.com/community/Screen) or [tmux](http://packages.ubuntu.com/natty/tmux) then you can re-attach to the session after logging in from anywhere.

---


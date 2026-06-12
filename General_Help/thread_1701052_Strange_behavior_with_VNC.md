---
title: "Strange behavior with VNC"
date: 2011-03-05
forum: General Help
---

### Post by jhogarth on 2011-03-05
I'm having a strange problem with VNC.  I have it installed and working except that when I try to open a file in an application such as GEdit, I get a segfault and the application closes.  This happens with any similar application under Gnome.  If I open a terminal, I can use Nano or Vim to open and update files.

I'm using Ubuntu server 10.10 with Gnome installed and Tightvncserver.  I'm connecting to the server with a Windows laptop.  This is all on my internal home network.

Any suggestions, I'm out of ideas where to look for this.  I doubt this is a memory issue, nothing else causes this failure.  Also, I have guests running under KVM that exhibit the same problem.

I should add that if I use the console at the server, this problem does not occur, it's only when I use VNC.

Thank you

---

### Post by pqwoerituytrueiwoq on 2011-03-06
be sure you have the server side of vnc running vino-server

---


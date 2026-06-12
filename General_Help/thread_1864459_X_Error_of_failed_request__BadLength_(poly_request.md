---
title: "X Error of failed request:  BadLength (poly request too large or internal Xlib length"
date: 2011-10-19
forum: General Help
---

### Post by debug01 on 2011-10-19
Hello

My problem is this ...

Initially I could not detect an iPod in my laptop with ubuntu 10, so, I upgraded my system, however, I don't know which package I upgraded (by mistake) and now I can't execute programs that were previously compiled in g++ using OpenGL (gl, glu, glut)

>>g++ -o program programSource.c -lGL -lGLU -lglut

Before upgrading, programs that I had compiled I could perform and display them without problems, but now, I can't do anything, I get the following error when I invoked this programs from a terminal:

X Error of failed request:  BadLength (poly request too large or internal Xlib length error)
  Major opcode of failed request:  153 (GLX)
  Minor opcode of failed request:  17 (X_GLXVendorPrivateWithReply)
  Serial number of failed request:  27
  Current serial number in output stream:  27

---


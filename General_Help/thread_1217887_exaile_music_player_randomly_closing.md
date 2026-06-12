---
title: "exaile music player randomly closing?"
date: 2009-07-20
forum: General Help
---

### Post by serious7 on 2009-07-20
Hey for some reason exaile music player randomly shuts off for no reason when I play songs. It just closes. I restart ubuntu and it continues to shuts off after playing a song for a few seconds. It does it randomly.

---

### Post by kpkeerthi on 2009-07-20
Run it from command prompt. It might print something useful in the console when it crashes.

---

### Post by mabt on 2010-12-03
I'm experiencing same problem here.
Here's the log:

"mabt@User-Ubuntu:~$ exaile
INFO    : Loading Exaile 0.3.2.0...
INFO    : Loading settings...
** Message: pygobject_register_sinkfunc is deprecated (GstObject)
INFO    : Loading plugins...
INFO    : Loading collection...
INFO    : Loading devices...
INFO    : Loading interface...
INFO    : Loading main window...
INFO    : Connecting main window events...
INFO    : Loading panels...
INFO    : Connecting panel events...
INFO    : Done loading main window...
INFO    : Playing file:///media/Hell/Musicas/Accept%20-%2022%20Album/Accept%20%5B1984%5D%20Balls%20To%20The%20Wall/01%20-%20Accept%20-%20Balls%20To%20The%20Wall.mp3
INFO    : Playing file:///media/Hell/Musicas/AC%20DC/AD%20DC%20-%20Back%20In%20Black/01%20-%20Hells%20Bells.mp3
python: ../../src/xcb_io.c:249: process_responses: Assertiva `(((long) (dpy->last_request_read) - (long) (dpy->request)) <= 0)' falhou.
Abortado
mabt@User-Ubuntu:~$ "

When it was playing the first song, the program didn't crash, but when i play the second song, it always crash.

Obs.: I'm using Ubuntu 10.10

---


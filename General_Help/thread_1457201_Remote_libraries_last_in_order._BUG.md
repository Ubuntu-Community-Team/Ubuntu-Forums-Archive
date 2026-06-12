---
title: "Remote libraries last in order. BUG?"
date: 2010-04-18
forum: General Help
---

### Post by Kaj Silander on 2010-04-18
Hi! This is my first post here so be nice :)

My girlfriend have a application she use at work. The application is reached from a
servermount with a script that mounts it and adds a LD_LIBRARY_PATH to its libraries.

The problem is at home where we dont have the same fast connection to server.....

When she mount the server share and gets the environment variables setup (LD_LIBRARY_PATH amongst others) the computer gets very laggy cause the computer looks for libs on server in first case even for local apps. Takes a eternity to start each app.

Is there any way to place the server libs last in order to look for libs?
(Dont tell me to place server libs in difrent order in LD_LIBRARY_PATH, its empty default)

Is there a way to make the libs worst case scenario lookup?

Thanx in advance. Note English aint my native language..... Im swedish.

---


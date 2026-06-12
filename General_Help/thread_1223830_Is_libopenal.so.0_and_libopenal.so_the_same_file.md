---
title: "Is libopenal.so.0 and libopenal.so the same file??"
date: 2009-07-26
forum: General Help
---

### Post by toleolu on 2009-07-26
My new version of FlightGear is bombing saying it can't find file libopenal.so.0.  When I go to usr/lib there is a file there named libopenal.so that is linked to libopenal.so.1 (which exists) but no file named libopenal.so.0  If these aren't the same files and I need so.0, did I loose this when I removed Pulse Audio and Esound?? I had to remove Pulse Audio because it was hosing FG.   If it turns out I need this file, can I download it somewhere without having to reinstall Pulse??  Thanks

---

### Post by toleolu on 2009-07-27
Really showed my Linux noob status on this one.  Solution was to create a symbolic link to libopenal.so.1. So:  ln -s /usr/lib/libopenal.so.1 /usr/lib/libopenal.so.0  Just thought I would post for what it's worth.

---


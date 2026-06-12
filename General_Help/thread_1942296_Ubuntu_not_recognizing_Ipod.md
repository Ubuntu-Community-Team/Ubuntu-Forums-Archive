---
title: "Ubuntu not recognizing Ipod"
date: 2012-03-17
forum: General Help
---

### Post by joshj70 on 2012-03-17
I have an ipod nano 3rd generation and a while back I let Banshee redo my ipod so I could add music to it with Banshee, but after I did that I seen a few glitches such as playlists not working and it having way to much space being taken from some random file, anyway I got tired of it and finally went to Windows and got on itunes and restored it to default, but when I got back on Ubuntu and plugged it in I got nothing. Banshee doesn't recognize it, gtkpod doesn't show it, and it doesn't even show up in nautilus, and I can't even find it with fdisk. Does anyone know how to make Ubuntu recognize my ipod again?

---

### Post by raja.genupula on 2012-03-17
please post the output of ```
lsusb
```

---

### Post by joshj70 on 2012-03-18
```
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 0461:4d15 Primax Electronics, Ltd Dell Optical Mouse
Bus 003 Device 002: ID 03f0:140c Hewlett-Packard 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 05ac:1262 Apple, Inc. iPod Nano 3.Gen
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by joshj70 on 2012-03-18
Well nevermind, it seems to have randomly started to work. Thank you though.

---

### Post by raja.genupula on 2012-03-18
you mean now all fine ?

---

### Post by joshj70 on 2012-03-18
Yeah, right after I posted it popped up and everything is working fine again. not sure what happened.

---

### Post by raja.genupula on 2012-03-19
that's great news ,please mark the thread as solved from thread tools .

---


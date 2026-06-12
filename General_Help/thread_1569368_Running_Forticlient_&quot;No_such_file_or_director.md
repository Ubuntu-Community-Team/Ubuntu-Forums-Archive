---
title: "Running Forticlient: &quot;No such file or directory&quot;, but the file IS there."
date: 2010-09-06
forum: General Help
---

### Post by The Altruist on 2010-09-06
Title says it all.
I'm trying to run Forticlient 4.0.2012 on a fresh-install of 64bit Lucid.
The instructions say run the forticlientsslvpn file as root. I <i>sudo ./forticlientsslvpn</i> and even use tab-completion.
"sudo: unable to execute ./forticlientsslvpn: No such file or directory"
I chmodded 777 ownership on the file, and chowned it to myself. Still not running.

I have the same program running just fine on the machine I'm posting this from.
Any thoughts y'all?

---

### Post by The Altruist on 2010-09-06
UPDATE:
OK, it's not what I thought it was.
I installed Tcl/TK 8.5.
Now I'm getting:
```
./forticlientsslvpn: error while loading shared libraries: libgtk-x11-2.0.so.0: cannot open shared object file: No such file or directory
```
I checked, and libGTK2.0-0_2.20.1 is installed, and the library file is available in /usr/lib. Hm...

---

### Post by dcstar on 2010-09-07
32-bit only software will not run in a 64-bit environment.

---

### Post by The Altruist on 2011-02-04
Sorry to resurrect this thread, but I figured it needed an answer. You're right, dcstar. Forticlient needs the ia32-libs package before it will run. It whines about the wrong ELF type, but it runs all the same, and runs just dandy.

---

### Post by JulienSalleyron on 2012-11-05
Same problem, I have just installed this and it works
```

sudo aptitude install ia32-libs-gtk 

```

---


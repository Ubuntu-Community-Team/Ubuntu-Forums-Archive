---
title: "starting kdm...?"
date: 2006-01-28
forum: General Help
---

### Post by jmxhgyZN8wK7 on 2006-01-28
i did a "server" install from the ubuntu 5.10 cd, logged in and typed ```
sudo apt-get install kdm kde-core
``` it finished and i had no idea what to do, so i restarted the computer in the hopes that kdm would start automatically (windows habit)... still only black and white text... so i typed ```
kdm
``` and got "Only root wants to run kdm..." typed ```
sudo kdm
``` and got nothing.

can anyone tell me how to start kdm?  (i don't really feel like using kubuntu-desktop or downloading a kubuntu cd.)

---

### Post by Jason_25 on 2006-01-28
sudo /etc/init.d./kdm start

---

### Post by jmxhgyZN8wK7 on 2006-01-28
it says "kdm already running."

---

### Post by Jason_25 on 2006-01-28
What happens when you push ctrl-alt-f7?

---

### Post by Peter76 on 2006-01-28
[QUOTE=Jason_25]What happens when you push ctrl-alt-f7?[/QUOTE]

Should be alt+F7; ctrl+alt+F7 is when you are already in a Window Manager; alt+F7 is from the command line ( not an Xterm though)

---

### Post by jmxhgyZN8wK7 on 2006-01-28
i tried both; nothing happens.

---


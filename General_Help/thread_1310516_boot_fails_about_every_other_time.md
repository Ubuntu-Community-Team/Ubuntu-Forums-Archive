---
title: "boot fails about every other time"
date: 2009-11-01
forum: General Help
---

### Post by brandon_h on 2009-11-01
using karmic

Just about every time I try to boot, on the first time, it fails and I get this

[IMG]http://ubuntuforums.org/www.brandonjhall.com/stuffs/login.jpg[/IMG][IMG]http://www.brandonjhall.com/stuffs/login.jpg[/IMG]

sorry about the quality, had to piece together three pics from my phone.

---

### Post by Monotoko on 2009-11-01
wait a moment, then type "exit"

Your root device just isnt quite ready when ubuntu wants it, needs to warm up :P

---

### Post by brandon_h on 2009-11-01
It takes quite a while to get to that point..

I get to the black screen with the white ubuntu logo. it sets there for a few moments....then goes to a black screen for a few moments....then finally what you see in the pic. all in all, takes quite a while.

---

### Post by Monotoko on 2009-11-01
I would still advise trying the exit command

If it works then you need to modify rootdelay

---

### Post by brandon_h on 2009-11-01
okay, thanks.

---

### Post by brandon_h on 2009-11-02
Typing exit only brings the exact same message up again. typing reboot starts a reboot and the desktop loads that way.

i changed the boot deal to 20 seconds and that did not solve the problem.

---


---
title: "why does my new arduino show up as /dev/ttyACM0"
date: 2011-10-22
forum: General Help
---

### Post by flyingsliverfin on 2011-10-22
I was wondering what kind of connection is made with my newly acquired Arduino Uno? In dmesg i can see it registered as "ttyACM0" and /dev/ttyACM0 exists...

The only tty's I've dealt with before are those than come up when i press ctr+alt+f1/f3...f6/f7. Im guessing its some kind of 'virtual' terminal?

---

### Post by dcstar on 2011-10-22
> **flyingsliverfin said:**
> I was wondering what kind of connection is made with my newly acquired Arduino Uno? In dmesg i can see it registered as "ttyACM0" and /dev/ttyACM0 exists...
.......

Because that is how Unix/Linux works with all I/O devices.

---


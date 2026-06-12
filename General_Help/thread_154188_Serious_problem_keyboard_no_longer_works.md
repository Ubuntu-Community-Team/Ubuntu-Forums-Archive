---
title: "Serious problem: keyboard no longer works"
date: 2006-04-02
forum: General Help
---

### Post by Ian Maxwell on 2006-04-02
I was just trying to move my /tmp directory onto a temporary filesystem, and so I erased everything currently in it before shutting down. (In retrospect I should have backed these files up, but I did not.)

Presumably as a result of this, my keyboard (PS/2) no longer works when I boot up Ubuntu. Mostly everything else works fine, although it's hard to test since I can't log into the GUI (I can SSH in to test everything else).

I could do something extreme like back up all my data and reinstall, but I was hoping I could just replace my missing /tmp files. Could I just replace them directly from the Ubuntu CD? If not, could I find them online somewhere?

(On another note, does it seem strange to anyone else that there are important files in /tmp?)

I've been posting a lot lately with a lot of dumb things I've done to myself, and I appreciate all the help I'm getting.

---

### Post by Ian Maxwell on 2006-04-03
A bit more information. I am getting the following two error messages during bootup (both have long strings of numbers before them that I can't write down before they scroll off the screen):
```

i8042.c: Can't read CTR while initializing i8042

usb 1-2: device not accepting address 2, error -71
```

It is very important that I get this fixed, and I would greatly appreciate any response to this.

---

### Post by Ian Maxwell on 2006-04-03
Still more more information: The plain 686 kernel boots just fine. Only the 686-smp kernel has problems. I tried reinstalling all 686-smp packages in Synaptic (since it was working fine until my /tmp-deleting rampage), but this has not helped.

Since I can at least boot my machine now, I'm no longer in a panic, but I'd still appreciate any ideas on what's going on (since I'd like to use the smp kernel).

---


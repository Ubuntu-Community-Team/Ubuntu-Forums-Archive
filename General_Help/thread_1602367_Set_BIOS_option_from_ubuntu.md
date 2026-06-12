---
title: "Set BIOS option from ubuntu?"
date: 2010-10-21
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2010-10-21
I noticed by bios has an setting for numlock but does not have it in the UI is there a way I can set it?
[IMG]http://i53.tinypic.com/2ntk07p.png[/IMG]
I am using numlockx now but the light does not come on but the function is active

---

### Post by pqwoerituytrueiwoq on 2010-10-22
Can I get an answer?

---

### Post by ironic.demise on 2010-10-22
There is no way to change the bios from an OS... that would be VERY dangerous.
Turn your pc off, turn it back on, boot into BIOS, set numlock to "on" and see if it works in Ubuntu.

---

### Post by drs305 on 2010-10-22
You can run this command to have Ubuntu remember the numlock status, although I think that is the default...

```
gconftool-2 -s -t bool /desktop/gnome/peripherals/keyboard/remember_numlock_state true
```

---

### Post by pqwoerituytrueiwoq on 2010-10-22
> **ironic.demise said:**
> There is no way to change the bios from an OS... that would be VERY dangerous.
Turn your pc off, turn it back on, boot into BIOS, set numlock to "on" and see if it works in Ubuntu.
there is no ui in the bios for it T_T

---


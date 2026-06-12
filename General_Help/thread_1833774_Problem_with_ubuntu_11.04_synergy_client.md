---
title: "Problem with ubuntu 11.04 synergy client"
date: 2011-08-26
forum: General Help
---

### Post by abowen500 on 2011-08-26
Hello,

I've installed synergy 1.4.3 on Ubuntu 11.04 32-bit.  I'm using this machine as the client.  It connects fine and everything seems to work except for the blasted control key.  I'll paste in the output from debug mode of synergy client while the client has keyboard/mouse focus.  When I press Ctrl-c all I receeve in terminal, for example, is a lowercase c.  The Alt keys are behaving similary.

The keycode for left_control matches what's in my xmodmap file (e.g. 25).  It seems as if this keypress isn't getting passed up from synergy to ubuntu.  Any ideas?

Output from synergyc in debug mode with control key depressed:
recv key down id=0x0000efe3, mask=0x0000, button=0x001d
mapKey efe3 (61411) with mask 0000, start state: 0000
find best:  0000 0000
best key index 0 of 1 (exact)
found key in group 0
state: 0000,0000,0000
flip: 0000 (0000 vs 0000 in 0000 - 0000)
desired state: 0000 0000,0000,0000
flip: 0000 (0000 vs 0000 in fffd - 6020)
mapped to 025, new state 0002
keystrokes:
  025 (00000000) down
recv key repeat id=0x0000efe3, mask=0x0000, count=1, button=0x001d
mapKey efe3 (61411) with mask 0000, start state: 0002
find best:  0002 0000
best key index 0 of 1 (exact)
found key in group 0
state: 0002,0000,0000
flip: 0000 (0002 vs 0000 in 0000 - 0000)
desired state: 0000 0002,0000,0000
flip: 0000 (0002 vs 0000 in fffd - 6020)
mapped to 025, new state 0002
keystrokes:
  025 (00000000) up
  discard autorepeat
  025 (00000000) down
  discard autorepeat

---

### Post by abowen500 on 2011-08-26
FIXED!  I installed Ubuntu with a spare keyboard that was configured with a different layout.  Everything works fine with the correct keyboard layout.

---


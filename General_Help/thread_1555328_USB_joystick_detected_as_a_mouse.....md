---
title: "USB joystick detected as a mouse...."
date: 2010-08-17
forum: General Help
---

### Post by Vanillalite on 2010-08-17
I have a gravis gamepad pro, and while Ubuntu recognizes the input device it's treated as another mouse control instead of an actual joystick.

Anyways to fix this? I looked around under system and didn't see anything that would let me maybe fix this.

I'm running Ubuntu 10.04 amd64, and I'm at a loss on where to go from here.

Thanks in advance! :D

---

### Post by Vanillalite on 2010-08-18
I found a bug list here and they have a temp fix at the bottom. I'm not following what I should be doing in the terminal though.

```
quickfix:
use the command xinput set-props <device-id> <option-id> 0
to set mouse events and keyboard events to false for the joystick/gamepad
the respective id can be found by running
xinput list
and
xinput list-props <device-id>
```

I can find that my device id using xinput list is id=8 for my gamepad. I don't know wtf they mean when they said option-id though? Do I need to type id=8 or can I just type 8 for my device-id?

---


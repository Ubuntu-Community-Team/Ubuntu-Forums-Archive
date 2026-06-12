---
title: "Using RCTRL as a TAB key"
date: 2011-07-15
forum: General Help
---

### Post by cpmman on 2011-07-15
I use the numeric block on the laptop quite a lot for entering numeric data.  To go to the next field for input the TAB key is used which requires the left hand or a long right hand travel.

Does anyone know how to re-program the right ctrl key to be another tab key which would allow single-handed data entry?

This should survive any program (I should choose an alternate for VM cursor purposes).

---

### Post by enimeizoo on 2011-07-16
Hello,
xmodmap lets you do that.

You will need to remove the control_R from the modifier, and then map it to the tab keysym. I don't have much time right now, so I won't give you teh details, but the man is well written.

You can have a look at keysymdef.h for existing keysyms. Not sure where it is, but 'locate' should tell you.
Good luck!

---

### Post by cpmman on 2011-09-24
> **enimeizoo said:**
> Hello,
xmodmap lets you do that.

You will need to remove the control_R from the modifier, and then map it to the tab keysym. I don't have much time right now, so I won't give you teh details, but the man is well written.

You can have a look at keysymdef.h for existing keysyms. Not sure where it is, but 'locate' should tell you.
Good luck!

Thank you for that - my apologies for such a delay in returning to this issue.
It simply needed the Control_R added into a .Xmodmap file in my  home user thus:-
```

keycode 105 = Tab ISO_Left_Tab Tab ISO_Left_Tab
```followed by a logout login.

---

### Post by LogicalDash on 2011-10-24
For future reference, you could have avoided the logout-login by entering this at a console:

```

xmodmap -e 'keycode 105 = Tab ISO_Left_Tab Tab ISO_Left_Tab'

```

---


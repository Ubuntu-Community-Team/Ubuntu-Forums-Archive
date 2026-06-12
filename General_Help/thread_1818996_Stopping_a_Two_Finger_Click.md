---
title: "Stopping a Two Finger Click"
date: 2011-08-05
forum: General Help
---

### Post by JoshuaBranson on 2011-08-05
I've got a laptop with a touchpad. When my cursor is in a text box (ie: this one or abiword or email) and I touch my touchpad with two fingers it automatically pastes whatever is on the "clipboard." How can I make it so when I touch my touchpad with two fingers it does NOT paste any text?

---

### Post by mikewhatever on 2011-08-05
> **JoshuaBranson said:**
> I've got a laptop with a touchpad. When my cursor is in a text box (ie: this one or abiword or email) and I touch my touchpad with two fingers it automatically pastes whatever is on the "clipboard." How can I make it so when I touch my touchpad with two fingers it does NOT paste any text?

In a terminal window, type **synclient -l | grep TapButton**.
If the output you get is something like the following,
```

    TapButton1              = 1
    TapButton2              = 2
    TapButton3              = 3

```

you can disable the two finger tap with **synclient TapButton2=0**.

If it works as expected, add the above command to startup applications to make the change persistent.

---


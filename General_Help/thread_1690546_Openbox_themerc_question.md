---
title: "Openbox themerc question"
date: 2011-02-18
forum: General Help
---

### Post by matt.rebo. on 2011-02-18
hi
does anyone know how to increase the px value of the interlaced function when writing a themerc for openbox?

to clarify...

typically the themerc has code like

```
# Active window
window.active.title.bg: Raised Gradient Vertical Interlaced
window.active.title.bg.color: #658fb5
window.active.title.bg.colorTo: #4d6982
window.active.title.bg.interlace.color: #7788cc
```the interlaced effect produces a kind of 10 lines effect going horizontally along the border...

question is how to set the px value of the interlaced function from say 1px to 4 px which would produce something like 4 horizontal lines instead of 10?

i've experimented with padding and checked the main openbox wiki and googled but no luck yet, so any help will be greatly appreciated? TIA.

---

### Post by urukrama on 2011-02-19
As far as I know, that is not possible.

---

### Post by matt.rebo. on 2011-02-19
> **urukrama said:**
> As far as I know, that is not possible.

Meh... what do you know? Not like you wrote one of the best blogs on the internet on the subject is it... :wink:

If I find any solution / hack, I'll post here... Thanks for the feedback.

---

### Post by urukrama on 2011-02-20
You could always post something on the Openbox mailing list. Perhaps one of the devs can help out.

---

### Post by FallenUnia on 2011-02-20
Not sure I'm getting what you want. Could you post the themerc file and some screenshots on what it looks like and what you want to accomplish?

As an ex OB user I might be of help.

---

### Post by urukrama on 2011-02-21
He wants to change the distance between the interlaced lines (make them further apart or closer together).

---


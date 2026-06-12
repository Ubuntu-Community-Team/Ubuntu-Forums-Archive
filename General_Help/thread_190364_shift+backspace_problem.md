---
title: "shift+backspace problem"
date: 2006-06-06
forum: General Help
---

### Post by smartalecks on 2006-06-06
When I press [Shift]+[Backspace] GDM resets. Why is this, and how do I change it? Its really annoying.

---

### Post by Poka64 on 2006-06-06
if you are using Glx/Compiz, try this, worked for me.

```
xmodmap -e "keycode  22 = BackSpace"
```

Edit: in a terminal ofc

---

### Post by bruce89 on 2006-06-06
It is a bug in XGL, try the thing in the post above.

---

### Post by firetux on 2006-06-06
Using the search(keywords: shift, backspace(not difficult to come up with)) I found 8 threads about exactly the same problem. 
Please use the search feature of the forums before you make a new thread.
This reduces the load of the forums, the bandwith has to be paid too.

---


---
title: "Help resetting DISPLAY property"
date: 2010-09-06
forum: General Help
---

### Post by DarkStorm_ on 2010-09-06
So I was fiddling around with things earlier today, trying to figure out how to use ssh to remotely view a desktop, and I accidentally set the DISPLAY property to something else using ```
export DISPLAY=something I can't remember
```

But I don't know how to set it back, nor what it should be set back to...

---

### Post by DarkStorm_ on 2010-09-06
Sorry for the double-post but I just fixed it using
```
export DISPLAY=":0.0"
```

---


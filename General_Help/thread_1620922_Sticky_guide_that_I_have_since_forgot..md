---
title: "Sticky guide that I have since forgot."
date: 2010-11-13
forum: General Help
---

### Post by fmuise on 2010-11-13
The guide included instructions to set my touch pad not to initialize for x amount of seconds after using the keyboard.
:)

Anyone know how to do this.

---

### Post by nothingspecial on 2010-11-13
Is this what you mean?

```
syndaemon -d -t -i 2
```

Change the 2 at the end to however many seconds you want.

Add that line to system > preferences > startup applications to make it permanent

---


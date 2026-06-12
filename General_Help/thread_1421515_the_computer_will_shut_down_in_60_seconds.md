---
title: "the computer will shut down in 60 seconds"
date: 2010-03-04
forum: General Help
---

### Post by utnu on 2010-03-04
When I click Shut Down, a popup pops up with the message 
*The computer will shut down in 60 seconds.*

How can I simply Shut Down, *with no popup* ?

---

### Post by wojox on 2010-03-04
Run this in the terminal:

```
gconftool-2 -s '/apps/indicator-session/suppress_logout_restart_shutdown' --type bool true
```

---

### Post by utnu on 2010-03-04
eyuh . . . it works.

a gracious Thank You

---

### Post by utnu on 2010-03-04
while you're here . . . how would one undo that ?

( for future reference, just in case )

Thank you very much.

---

### Post by sisco311 on 2010-03-04
```
gconftool-2 -s '/apps/indicator-session/suppress_logout_restart_shutdown' --type bool false
```

Or you can use gconf-editor (a GUI application) to change the value of the /apps/indicator-session/suppress_logout_restart_shutdown gconf key.

---

### Post by utnu on 2010-03-04
I will try those out later.

Thank you very much

---


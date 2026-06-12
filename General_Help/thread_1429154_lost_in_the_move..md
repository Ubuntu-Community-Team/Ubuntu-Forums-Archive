---
title: "lost in the move."
date: 2010-03-13
forum: General Help
---

### Post by themarker0 on 2010-03-13
When i was running Ubuntu 9.04 i could use the scroll on my house or keyboard to switch windows. I can do longer do this in 9.10 Any reason why not?

---

### Post by wojox on 2010-03-13
Unfortunately it isn't enabled by default.
Enable visual effects.
Install:

```
sudo apt-get update && sudo apt-get install compizconfig-settings-manager
```

After installation it's in system preferences.
Then open and navigate to:
Section 'Workspace'.
Just enable this plugin, that should be all.

---

### Post by themarker0 on 2010-03-13
Where is the workspace located? I can't find in in the compizconfig settings area.

---

### Post by wojox on 2010-03-14
You're right I can't find it now either. I must have left something out.

Press Alt+F2 and type in: **gconf-editor**

Go to apps > compiz > plugins > vpswitch > allscreens > options

See if **initiate_button** has the value **Button2**

---

### Post by stinkeye on 2010-03-14
To rotate cube with the scroll wheel when the mouse is on the desktop...

---

### Post by themarker0 on 2010-03-14
Thank you two, i have it working now.

---


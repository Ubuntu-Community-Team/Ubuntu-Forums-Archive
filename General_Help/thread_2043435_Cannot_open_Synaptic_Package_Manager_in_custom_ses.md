---
title: "Cannot open Synaptic Package Manager in custom session"
date: 2012-08-16
forum: General Help
---

### Post by xxnishantxx on 2012-08-16
Hi, I'm using a custom session with Unity on a minimal install of Ubuntu 12.04. The problem is that I can't open Synaptic by clicking on the launcher or from the Dash. It does not even prompt for the password.

However, if I run ```
gksudo synaptic
```, it runs just fine. Also, if I run ```
synaptic-pkexec
``` from the terminal, it asks for my password and launches synaptic fine. 

The launcher works fine in the Classic Gnome session, so I think the problem might have something to do with some daemon or something missing in my custom session. These are the contents of my ~/.xsession :

```
#!/bin/bash
gnome-terminal &
compiz ccp &
gnome-settings-daemon
```

Please advice :)

---

### Post by xxnishantxx on 2012-08-16
bump

---


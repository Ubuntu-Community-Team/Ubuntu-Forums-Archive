---
title: "Auto-start command"
date: 2011-12-12
forum: General Help
---

### Post by Ph1b on 2011-12-12
Hey,

just figured out this command xinput set-button-map 12 1 2 3 5 4 to invert my scrolling. How can I autostart it? Just added it to the rc.local but that doesn't work.

---

### Post by VCoolio on 2011-12-12
I'm not sure when rc.local is read, but that command needs to be run when X is up. Try ~/.profile (which is read once, after login), maybe with some delay, like: sleep 5 && xinput etc

---


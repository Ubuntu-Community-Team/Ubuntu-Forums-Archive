---
title: "Different startup programs on different power supplies (AC / Battery), possible?"
date: 2010-06-12
forum: General Help
---

### Post by Asagrim on 2010-06-12
For example if my netbook runs on AC i would like it to start emesene, Skype etc. on system startup, but if it runs on Battery i want different startup programs - less of the same programs basically -.

Is there some script i could use for this purpose?

---

### Post by Asagrim on 2010-06-12
SOLVED!

I also spiced it up a little:

sleep 15 #to wait for an internet connection to be established
if acpitool  | grep on-line && eval "ping -c 1 www.google.com"; then
emesene & skype
fi

---


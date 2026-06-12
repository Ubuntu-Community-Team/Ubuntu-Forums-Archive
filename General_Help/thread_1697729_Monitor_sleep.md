---
title: "Monitor sleep"
date: 2011-03-01
forum: General Help
---

### Post by ryezs on 2011-03-01
Hello
Problem was that the screen went black. The screensaver and the power manegment was off. 

found the solution i another thread

I added these lines to xorg.conf
```
Section "ServerFlags"
    Option      "blank time" "0"
    Option      "standby time" "0"
    Option      "suspend time" "0"
    Option      "off time" "0"
EndSection
```

---


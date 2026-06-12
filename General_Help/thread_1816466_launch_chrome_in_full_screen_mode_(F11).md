---
title: "launch chrome in full screen mode (F11) ?"
date: 2011-08-02
forum: General Help
---

### Post by cyberjar09 on 2011-08-02
Google Chrome	12.0.742.124 (Official Build 92024)
WebKit	534.30 (branches/chromium/742@89068)
V8	3.2.10.21
Flash	10.3 r181
User Agent	Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/534.30 (KHTML, like Gecko) Chrome/12.0.742.124 Safari/534.30
Command Line	 /opt/google/chrome/google-chrome --enable-plugins --flag-switches-begin --flag-switches-end

Operating System:Ubuntu 11.04 
Extensions installed: Apture, Google Dictionary, LastPass, Mail checker Plus, Scroll to Top, What font

I would like to start chrome in full screen mode (F11). Launching chrome from the terminal using "google-chrome --kiosk --incognito" only results in a regular sized incognito window. 


I launch chrome on startup using a script ```
sh -c 'sleep 5 && /opt/google/chrome/google-chrome'
``` but I would also like to launch it straight into full screen mode. Is there any way of emulating the F11 keypress?

Thanks in advance.

---

### Post by akoskm on 2011-08-02
```

#!/bin/bash
xdotool key F11

```

---

### Post by cyberjar09 on 2011-08-02
> **akoskm said:**
> ```

#!/bin/bash
xdotool key F11

```

incredible! thank you very much akoskm! 

thread marked solved.

---


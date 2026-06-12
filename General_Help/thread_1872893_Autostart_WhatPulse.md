---
title: "Autostart WhatPulse"
date: 2011-10-31
forum: General Help
---

### Post by Macrotus on 2011-10-31
Hi all

I have downloaded WhatPulse from whatpulse.org. It's the Linux x86 version. If I go to System -> Preferences -> Autostart programs (or something, my system isn't in English) and add WhatPulse it will start when Ubuntu starts. There is one problem: WhatPulse won't work without system tray (that bar on the top) and the gnome-panel isn't loaded before Ubuntu starts WhatPulse. Then I tried the following...

```
#!/bin/sh
sleep 10s
./WhatPulse
```

I saved it as autostartwhatpulse.sh to folder X where WhatPulse is also located. I created a new autostart program and I gave it this command:

```
sh /home/.../x/autostartwhatpulse.sh
```

The sh file has rights to be executed, but it won't work.

What should I do? Help?

Edit. Fixed. I don't know why, but I needed to add the full path /home/.../x/WhatPulse to the sh-file.

---


---
title: "&quot;Make&quot; doesn't work"
date: 2006-05-31
forum: General Help
---

### Post by Adanufgail on 2006-05-31
Hey. I'm realtively new to install things. I downloaded Chromium from the Ubuntu Wiki, installed SDL via the package manager, and ./configured worked fine. However, I typed "make" and got the following message
"bash: make: command not found"

I looked around for an answer and tried sudo checkinstall, got the same result. Thanks for the help.

---

### Post by user1397 on 2006-05-31
[quote=Adanufgail]Hey. I'm realtively new to install things. I downloaded Chromium from the Ubuntu Wiki, installed SDL via the package manager, and ./configured worked fine. However, I typed "make" and got the following message
"bash: make: command not found"

I looked around for an answer and tried sudo checkinstall, got the same result. Thanks for the help.[/quote]
For the make command, you need to install build-essential: ```
sudo aptitude update && sudo aptitude install build-essential
```
The checkinstall package is just for the sudo checkinstall command, while the make command (which comes before the sudo checkinstall command) comes from the build-essential package.

---

### Post by Adanufgail on 2006-05-31
Thanks!

---


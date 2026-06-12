---
title: "Wine question"
date: 2011-04-16
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2011-04-16
When you set the audio to use emulation instead of full in wine config what files is that stored in?
i am using a program that uses its own ported version of wine and it kills my sound when u open it
changing that setting appears to fix it
if i know where the file is in the real wine i may be able to find int in this app's files
edit:
added this to user.reg
```
[Software\\Wine\\DirectSound] 1302972032
"HardwareAcceleration"="Emulation"

[Software\\Wine\\Drivers] 1302807709
"Audio"=""
```

---


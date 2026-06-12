---
title: "confused as to how to get Xlink kai on Ubuntu"
date: 2009-08-30
forum: General Help
---

### Post by flamingrevolver on 2009-08-30
i'm not quite sure how to install xlink Kai and so far no other forums have helped me.. i'm rather new to all this Ubuntu/linux stuff so its basically like another language haha.. but i found some forums that told me to put my kaid file in the bin folder and the kaid.conf into the etc folder and when i try to run it by going to the bin folder in terminal and typing ./kaid this comes up... 

> KAID: You're not root, sorry...and another forum i read said to try sudo ./kaid  and when i try that it comes up like

> KAID: Kai Engine for Linux is initialising...
WARNING: Unable to open engine persist data file (/tmp/kaiEnginePersist.txt)
KAID: Kai Engine for Linux is starting...
THREAD: Engine thread started...
KAID: Failed to create UI socket...and i'm not sure what to do apparently.. but i'm guessing i'm missing the kaiEnginePersist.txt file or something... and maybe there's another problem.. i'm not sure but could someone try to help me figure this out?

---

### Post by lan_rogers_book on 2009-11-21
The problem lies in the "WARNING: Unable to open engine persist data file (/tmp/kaiEnginePersist.txt)".

I ran into the same problem, I kaid once and it failed every time afterwards, you need to manually delete the /tmp/kaiEnginePersist.txt file or set the ownership and permissions to something that's not root.

---


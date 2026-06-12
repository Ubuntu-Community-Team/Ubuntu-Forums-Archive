---
title: "Creating a .tgz file"
date: 2011-01-17
forum: General Help
---

### Post by TBhX£2760R8@nK7§r on 2011-01-17
Okay, I understand that I'm probably just being an idiot here, but for the past thirty minutes of searching and trying, I cannot figure out what I'm doing wrong.

```
#!/bin/sh
DATE=$(date +%m/%d/%y)
tar zvcf /home/mark/Minecraft/worldbackups/world.$DATE.tgz /home/mark/Minecraft/Public
```This give the output of

```
mark@kalle-desktop:~/Minecraft/Exec$ sh save.sh
tar: Removing leading `/' from member names
/home/mark/Minecraft/Public/
/home/mark/Minecraft/Public/default.html
/home/mark/Minecraft/Public/world.png
tar: /home/mark/Minecraft/worldbackups/world.01/17/11.tgz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
```If anyone could please tell me what I'm doing wrong, it would be greatly appreciated.

---

### Post by Smart Viking on 2011-01-17
Use this instead:
```
#!/bin/sh
DATE=$(date +%m-%d-%y)
tar zvcf /home/mark/Minecraft/worldbackups/world.$DATE.tgz /home/mark/Minecraft/Public
```

---

### Post by Smart Viking on 2011-01-17
Use this instead:
```
#!/bin/sh
DATE=$(date +%m-%d-%y)
tar zvcf /home/mark/Minecraft/worldbackups/world.$DATE.tgz /home/mark/Minecraft/Public
```

---

### Post by Smart Viking on 2011-01-17
Use this instead:
```
#!/bin/sh
DATE=$(date +%m-%d-%y)
tar zvcf /home/mark/Minecraft/worldbackups/world.$DATE.tgz /home/mark/Minecraft/Public
```

---

### Post by TBhX£2760R8@nK7§r on 2011-01-17
Thanks, that works.

---


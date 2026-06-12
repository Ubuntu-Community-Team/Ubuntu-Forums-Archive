---
title: "sh script automatically open konsole window"
date: 2011-05-29
forum: General Help
---

### Post by iclestu on 2011-05-29
i have a simple sh script. It executes ok by clicking in dolphin but I would like it to automatically open a konsole window and execute in there so that I could see the output. Is this possible?

---

### Post by ankspo71 on 2011-05-29
Hi, you can start the command by using "konsole -e" which tells the command to open konsole and execute the command.

```
konsole -e <command>
```

```
#!/bin/sh

konsole -e top
```

Hope this helps.

---

### Post by iclestu on 2011-05-29
> **ankspo71 said:**
> Hi, you can start the command by using "konsole -e" which tells the command to open konsole and execute the command.

```
konsole -e <command>
``````
#!/bin/sh

konsole -e top
```Hope this helps.

many thanks

---


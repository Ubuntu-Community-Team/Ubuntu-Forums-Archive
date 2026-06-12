---
title: "File space"
date: 2011-04-04
forum: General Help
---

### Post by Gamegoofs2 on 2011-04-04
The wubi install of Ubuntu is saying it only has 125 MB left. I gave the install 10 GB to start with. I know the OS takes about 3 GB and I didn't install 7 GB worth applications. I'm thinking some how it confused itself. I've done run the Disk Analysis And it's rather confusing, but it seems to be looking at more then its alloted 10 GB.

---

### Post by bcbc on 2011-04-04
Run the disk usage analyzer as root: Alt-F2 gksu baobab

Stop it, go to edit preferences, and deselect /host (as this will scan the host windows partition).

That should explain exactly where the 7GB are going.

---

### Post by coffeecat on 2011-04-04
Have you any files in trash that you haven't deleted from trash? Also, have you ever deleted any files with a gksudo nautilus root browser? If so, the deleted files will be in root's trash.

If you've done the latter, have a look in /root/.local/share/Trash. You'll need a gksudo nautilus window to be able to browse there.

---

### Post by Rubi1200 on 2011-04-05
Additionally, try this command in the terminal:

```
df -H
```

---

### Post by Gamegoofs2 on 2011-04-06
Ok here's a screenshot of what the disk analyzer gave. It  looks like nothing is taking up space.

Maybe I do have space...and maybe it was just a glitch. I don't remember getting a warning when I logged on.

Thanks for your help.

---

### Post by bcbc on 2011-04-06
You just scanned /root
Scan / or press the disk icon

---

### Post by techunit on 2011-04-06
Your looking at the wrong place look at "/" instead. That will tell you what to be looking for.

---


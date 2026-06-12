---
title: "No such file or directory"
date: 2012-01-10
forum: General Help
---

### Post by DJ . on 2012-01-10
I put in the correct directory in the terminal and it worked fine, but when I made a launcher in the gnome-panel it says "no such file or directory." I checked it many times and each time it worked for the terminal but not the launcher. How can I fix this?

---

### Post by mcduck on 2012-01-10
Are you using full path from the root of the filesystem?

If you just open a terminal and run the command, the directory might open since you are already in your home directory when running the command so a path relative to that location would work. The laucher however needs a full path instead.

Something like this:
```

/home/mcduck/Programs/Minecraft/minecraft.sh
```

(If I just open a terminal then running "Programs/Minecraft/minecraft.sh" works since I'm already in /home/mcduck when executing the command)

---


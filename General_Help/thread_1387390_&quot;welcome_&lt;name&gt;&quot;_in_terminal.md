---
title: "&quot;welcome &lt;name&gt;&quot; in terminal"
date: 2010-01-21
forum: General Help
---

### Post by Dayofswords on 2010-01-21
is there a way i can set up a script or something so that when i open a terminal it says like
"Welcome <Username>, its <time> on <date>, you should go do your homework instead of this..."

i know this is basically useless, but i was wonder what ways i could customize it

---

### Post by sisco311 on 2010-01-21
Append the ~/.bashrc file with something like:
```
echo -e "Welcome $USER, it's $(date +%r) on $(date +%D),\nyou should go do your homework instead of this..."
```

---

### Post by Dayofswords on 2010-01-21
worked perfectly, thank you so much:D

---


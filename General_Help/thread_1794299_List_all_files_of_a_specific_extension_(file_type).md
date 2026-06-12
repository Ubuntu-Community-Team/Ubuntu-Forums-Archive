---
title: "List all files of a specific extension (file type)"
date: 2011-06-30
forum: General Help
---

### Post by Adbekunkus on 2011-06-30
Hi all. I really need to know how to do this: I want a list of all my mp3 files (or any other kind of file, actually) telling me HOW MANY OF THEM I have in my computer. I tried with both find and locate commands in terminal, but they don't tell me how many files I have. Please, I'd really appreciate help on this one. Thanks!

---

### Post by Ozymandias_117 on 2011-06-30
```
locate -ci .mp3
```

---

### Post by WorMzy on 2011-06-30
```
find / -iname "*.mp3" | wc -l
```

is another method, and isn't limited to one filesystem by default.

---


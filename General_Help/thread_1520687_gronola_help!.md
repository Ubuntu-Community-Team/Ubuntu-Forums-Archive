---
title: "gronola help!"
date: 2010-06-29
forum: General Help
---

### Post by itsjoshgrant on 2010-06-29
ok i have horrible battery life on my laptop (like an 1 hour and 5 mins) so i tried downloading [http://grano.la/](http://grano.la/) and i didnt know how to download with bash, but i did the "manual" way and it kinda worked... i mean i followed all the instructions and i checked and its in my software sources, but when i go to the software center its not there on the left pane.what should i do

---

### Post by Noz3001 on 2010-06-29
Try

```
sudo apt-get update && sudo apt-get install granola granola-gui
```

---

### Post by itsjoshgrant on 2010-06-29
> **Noz3001 said:**
> Try

```
sudo apt-get update && sudo apt-get install granola granola-gui
```

yep, thanks man
had to reverse order and do as 2 separate actions but worked!

---


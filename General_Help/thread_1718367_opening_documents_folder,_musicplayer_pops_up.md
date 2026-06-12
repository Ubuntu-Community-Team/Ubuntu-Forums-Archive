---
title: "opening documents folder, musicplayer pops up"
date: 2011-03-31
forum: General Help
---

### Post by DAIVD on 2011-03-31
hello everyone!

I have this tiny problem, not really annoying but I havent been able to fix it, so ill just post it here.
When I wish to go to a folder listed in the places section in the upper panel, automaticly music player pops up. This is also happens when i want to open a download folder in transmission. Folder doesnt open, only way to go there is by computer on desktop. 

Does anyone have an idea how to get rid of this?

greetings, David

---

### Post by ~Plue on 2011-03-31
press alt+F2 to bring up the run dialog,
enter,
```
gedit .local/share/applications/mimeapps.list
```then delete the line *'inode/directory=........' *and save the file

-hope this helps

---

### Post by DAIVD on 2011-03-31
thanks a lot, worked to perfection!

---


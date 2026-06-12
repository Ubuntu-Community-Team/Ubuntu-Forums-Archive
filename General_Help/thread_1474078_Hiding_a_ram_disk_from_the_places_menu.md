---
title: "Hiding a ram disk from the places menu"
date: 2010-05-05
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2010-05-05
just wondering if it can be done
i have 2 of them in there
one for chrome and one for firefox

---

### Post by solitaire on 2010-05-05
What I did was mount /tmp as  ram drive and point ~/.cache (& ~/.thumbnails) to the /tmp folder
(I had a small script to recreate the folders in the ram drive every boot).
```
# Temporary File System
none /tmp tmpfs size=128M,nr_inodes=200k,mode=01777 0 0
```

---

### Post by pqwoerituytrueiwoq on 2010-05-05
i assume that is in your fstab file
how would i modify this?
```
#firefox on RAM
firefox /home/NAME/.mozilla/firefox/t2jwdsde.default tmpfs size=125M,noauto,user,exec,uid=1000,gid=1000 0 0
#chrome cache on RAM
chrome /home/NAME/.cache/google-chrome/Cache tmpfs size=55M,noauto,user,exec,uid=1001,gid=1001 0 0
``` uid and gid are supposed to be unique right?

---

### Post by WorMzy on 2010-05-05
uid is userID, gid is groupID, you want them to be the userID and groupID of the user/group you want to have ownership of the mounted device. 1000 is the default user and group.

---


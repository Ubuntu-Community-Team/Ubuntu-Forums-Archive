---
title: "How to transfer my settings all users in KDE4"
date: 2010-11-04
forum: General Help
---

### Post by wrix on 2010-11-04
Hello, I wanted to know a way to transfer all my KDE4 settings to all users in the system. I have tried to copy the settings to /etc/skel but the only problem I am having is whenever any new user tries to access their home folder, they come to my home folder because link to home folder is "file:///home/<my user name>". Please help in this regards. Thanks.

---

### Post by Zorael on 2010-11-04
I think /etc/skel is the right approach, yes. Hm.

Have you tried going through the settings files manually? Search for occurences of /home/*<yourusername>* and try with replacing them with **$HOME**. Dolphin seems to understand '**file:/$HOME**' at least, so likely every KDE program using the file:/ kioslave should too.

```
$ grep -Rn "/home/*<yourusername>*" /etc/skel/*
```

---


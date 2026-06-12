---
title: "Applications Folder?"
date: 2012-07-05
forum: General Help
---

### Post by switchfoot123 on 2012-07-05
I know that this is a total noob question and it's probably right in front of my face.

But.

Is there a folder located in the file browsing 'n such where it stores applications such as firefox, thunderbird, ubuntu one, etc? Someplace where I can browse through all of the apps and features.

---

### Post by msammels on 2012-07-05
Best way to do this is to click the Ubuntu icon on the launcher and click the second icon, under "Applications" hit "See X more results".

Files are usually stored in /usr/bin and /usr/sbin

---

### Post by GreatDanton on 2012-07-05
Also one good command for your terminal is 
```
which <the name of application>
```

You will get directory where is application located.

Regards.

---

### Post by codemaniac on 2012-07-05
```
dpkg --get-selections | grep ***app_name***
```

will list if the application is installed in your system .

---


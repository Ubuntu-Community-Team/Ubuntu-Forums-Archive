---
title: "root's file in user's home"
date: 2012-03-26
forum: General Help
---

### Post by Subidubi32 on 2012-03-26
I have a folder owned by the root user in my home directory. The problem, that I cannot reach it, because, if I open nautilus as root, I cannot see the folder, cause it is in my home folder not in the root's. Funny thing that the Heroes3 created it, with sudo permission. Any Idea how could I open it?

---

### Post by codemaniac on 2012-03-26
Just grant the necessary permissions on the folder , so that your less priviledged user can access it .You can execute the chmod with recursive switch , so that the directories and file under it , can enjoy the same security .
```
sudo chmod -R a+rx *your_folder_name*
```

---

### Post by Subidubi32 on 2012-03-26
Thank you very much, now it's accessable! :) Solved

---


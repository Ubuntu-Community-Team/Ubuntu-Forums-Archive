---
title: "Exaile will not start.. unless..."
date: 2010-06-14
forum: General Help
---

### Post by serbforce on 2010-06-14
Hello, i have problem with my favorite music player Exaile. It wont start from the shortcut in the menu, but when i do ''sudo exaile'' in termianl, then it starts. How can i fix this, i didnt mess with anything, it just started making trouble :). Thank you very much in advance.

- serbforce

---

### Post by sisco311 on 2010-06-14
[http://psychocats.net/ubuntu/graphicalsudo](http://psychocats.net/ubuntu/graphicalsudo)

Restore the ownership of the config files:
```
sudo chown -R $USER: **~/.local/share/exaile**
sudo chown -R  $USER: **~/.config/exaile**
sudo chown -R $USER: **~/.cache/exaile**
```

---


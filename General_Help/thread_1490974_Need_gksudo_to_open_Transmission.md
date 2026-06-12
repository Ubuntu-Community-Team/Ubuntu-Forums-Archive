---
title: "Need gksudo to open Transmission"
date: 2010-05-23
forum: General Help
---

### Post by shai3421 on 2010-05-23
When I try to open Transmission I get a message: "Couldn't open "/home/shai/.config/transmission/lock": Permission denied", and the only way to open it is by using gksudo.

I read on another thread that I need to delete that file, but the file doesn't exist.

What should I do?

Thanks.

---

### Post by sisco311 on 2010-05-23
Is the config directory owned by your user?
```
sudo chown -R $USER: ~/.config/transmission
```

---

### Post by shai3421 on 2010-05-23
Thanks, that fixed it.

---


---
title: "Problem With an archive..."
date: 2010-04-02
forum: General Help
---

### Post by Psumi on 2010-04-02
I have this archive from gnome-look (an icon theme set called Voyager Simple Dark) and tar can't seem to untar it:

```
cd /home/psumi/.icons && tar -x Voyager-Simple-Dark.05.tar.gz
```

Will hang on the second command.

---

### Post by juancarlospaco on 2010-04-02
tar -xvf ./Voyager-Simple-Dark.05.tar.gz

---

### Post by FuturePilot on 2010-04-02
You need the -f option.

> f, --file ARCHIVE
use archive file or device ARCHIVE

---

### Post by Psumi on 2010-04-02
Thanks people.

---

### Post by juancarlospaco on 2010-04-02
*You are welcome...*

---


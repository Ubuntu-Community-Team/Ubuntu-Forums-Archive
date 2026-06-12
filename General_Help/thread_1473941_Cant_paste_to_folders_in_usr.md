---
title: "Cant paste to folders in usr"
date: 2010-05-05
forum: General Help
---

### Post by teejayuu on 2010-05-05
Hi

I'm a Linux newbie.  I have a Dell mini 10 that came with ubuntu 8.04.  I have today installed Lucid Lynx and am trying to paste fluendo  codecs to /usr/lib/gsteamer-0.10 and the paste command, amongst others, is disabled.  I think this is down to permissions, ss there any way to override this?

Tony

---

### Post by cdenley on 2010-05-05
Software should ALWAYS be installed from the repository whenever possible. You shouldn't be pasting files to install codecs.
```

sudo apt-get install gstreamer0.10-fluendo.*

```

---


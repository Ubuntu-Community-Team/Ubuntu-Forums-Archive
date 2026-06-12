---
title: "I kinda deleted /bin/sh..."
date: 2010-03-13
forum: General Help
---

### Post by the_damian_child on 2010-03-13
I sudo mv'd a script into '/bin/sh' 
I know, it was stupid (I don't even know if you put scripts in /bin, I'm a script noob)
but it's early and I wasn't thinking straight.
Help?

---

### Post by jocko on 2010-03-13
/bin/sh is just a link to /bin/dash, so this command should fix it for you:
```
sudo ln -s /bin/dash /bin/sh
```

---

### Post by the_damian_child on 2010-03-13
phew
thanks!
I almost did a clean install!
No wonder I couldn't find anywhere to download it >_<
Again, many thanks

---


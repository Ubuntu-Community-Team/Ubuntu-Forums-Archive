---
title: "Ubuntu/Mac help"
date: 2010-06-26
forum: General Help
---

### Post by taunnt on 2010-06-26
Hello I have a comp with Snow Leopard/Windows/Ubuntu 10.4 on it. What I'm trying to do is set permissions to let me copy files from  the Snow Leopard partition. I use to be able to. Now I get Permission denied. What do I need to do to set up permissions to the hfs+ journaled partition?

Thanks

---

### Post by Smart Viking on 2010-06-26
Launch this command from the terminal:

```
gksudo nautilus
```

That should open the file browser with the super user, see if you have access then. :)

---


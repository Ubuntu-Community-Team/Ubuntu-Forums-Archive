---
title: "How to list recently upgraded packages"
date: 2010-05-18
forum: General Help
---

### Post by hawthornso23 on 2010-05-18
I've just diagnosed and replaced faulty memory which was causing programs to terminate suddenly. Running memtest showed that I actually had over half a megabyte of faulty memory. It is astonishing to me that my system was running at all. 

I am very glad that I figured out what was going on before trying to upgrade to lucid. The upgrade process may not have gone well. Now that I've got my memory fixed, I'd like to reinstall all packages which were updated over the last month just in case they may have been corrupted by the faulty memory. How can I obtain a list of recently updated packages?

---

### Post by philinux on 2010-05-18
Either fire up update manager or in a terminal.

```
sudo apt-get update && sudo apt-get upgrade
```

The system will sort itself out.

---

### Post by hawthornso23 on 2010-05-18
OK - nothing upgraded.

So what you are basically saying is that the system is fully capable of detecting and dealing with possible corruption of packages during update because of faulty memory, and I shouldn't worry about it. That is pretty impressive that it can cope with unreliable memory like that. Wow!

Looks like I'm sorted then. Thanks.

---

### Post by philinux on 2010-05-18
If during the last month any package failed to update/upgrade correctly it would have given error messages out at the time.

Memory problems tend to crash things so if it crashed during an update it would let you know.

---


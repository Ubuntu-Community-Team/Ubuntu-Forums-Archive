---
title: "Stop module from loading?"
date: 2009-07-19
forum: General Help
---

### Post by JockVSJock on 2009-07-19
I'm trying to stop the floppy module from loading into the kernel, because I don't have a floppy drive on my computer. 

I created an entry under the following:  /etc/modprobe.d/blacklist 

```
 blacklist floppy 
```

However once I rebooted, it was still loaded.

What is the best way to prevent this module from loading?

---


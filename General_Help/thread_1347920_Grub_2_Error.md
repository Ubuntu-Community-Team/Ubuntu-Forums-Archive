---
title: "Grub 2 Error"
date: 2009-12-06
forum: General Help
---

### Post by User3k on 2009-12-06
I had an IDE drive on my computer that I recently took off. It was seen as SDD. When I run update-grub I get a lot of these errors,

```
error: cannot open `/dev/sdd' while attempting to get disk size
```

What do I need to edit to get it to stop looking for sdd?

---

### Post by User3k on 2009-12-06
Found it. There was a line in /boot/grub/device.map, "(hd3)	/dev/sdd" I just deleted it and it is fine now.

---


---
title: "find BIOS Bug details"
date: 2009-09-01
forum: General Help
---

### Post by Vishnu V on 2009-09-01
Hai,
When my system boots it shows a message MP BIOS BUG and report it.It shows for a while and i cannot get more details.How can i find more details of this bug

Thanks in advance

---

### Post by P4man on 2009-09-01
you can run "dmesg" in a terminal to view the errors shown during boot. To save it to a file run
```

dmesg > dmesg.txt
```

then you can perhaps google on it for more info, or try if you can update your bios.

---


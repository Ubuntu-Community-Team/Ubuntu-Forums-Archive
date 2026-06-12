---
title: "System monitor seems inaccurate"
date: 2010-10-31
forum: General Help
---

### Post by mcsheffrey on 2010-10-31
When I check the "system monitor" it show about 560M of memory being used of the 1G that I have. When I check it with VMSTAT or TOP it says that I'm using almost my max,a bit over 1G. Now I'm more confident in VMSTAT than the UBUNTU system monitor, but would like to know if any else is seeing this problem. Just to add to this, I guess my concern is should I be adding more memory to the desktop.  Tks. Roy

---

### Post by dcstar on 2010-11-01
> **mcsheffrey said:**
> When I check the "system monitor" it show about 560M of memory being used of the 1G that I have. When I check it with VMSTAT or TOP it says that I'm using almost my max,a bit over 1G. Now I'm more confident in VMSTAT than the UBUNTU system monitor, but would like to know if any else is seeing this problem. Just to add to this, I guess my concern is should I be adding more memory to the desktop.  Tks. Roy

MiB <> MB.

---

### Post by HiImTye on 2010-11-01
easy one to figure out.
open up top or htop or whatever you use.
look at the memory used at the top.
now, look at the percentage of memory used by each program
these don't add up to the same amount

edit: actually htop is reporting the correct amount

---


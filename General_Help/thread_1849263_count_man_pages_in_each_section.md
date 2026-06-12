---
title: "count man pages in each section"
date: 2011-09-24
forum: General Help
---

### Post by yasirsaleem106 on 2011-09-24
Hi all,
I want to count total number of man pages in each section(there are 8 sections I want to get count of all of them individually).
Kindly help me.

Regards,

Yasir Saleem

---

### Post by Lars Noodén on 2011-09-24
My guess is that the following would find and count them:

```

find /usr/share/man -type f -print | wc -l

```

That's for the grand total.  You can modify the path accordingly if you want subtotals.

---


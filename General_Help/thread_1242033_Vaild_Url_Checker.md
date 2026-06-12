---
title: "Vaild Url Checker"
date: 2009-08-16
forum: General Help
---

### Post by Chamillionaire2 on 2009-08-16
What's Up?

Getting straight down to brass tacks here, Does anyone happen to know how to check for vaild working links, Using pearl through a file?

Thanks Bye.

---

### Post by lisati on 2009-08-17
Call up "ping" and check its status?

---

### Post by nikhilk on 2009-08-17
> **lisati said:**
> Call up "ping" and check its status?

A ping can confirm whether a host is up or not. But it cannot check for a specific link on the host running a web server which what the OP wanted to know, I assume.

Chamillionaire2,
You could use curl or wget in spider mode to accomplish what you want. I think both can read the links to be checked from a file (I know of wget -i <file_with_links_to_be_checked>).

---


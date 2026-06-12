---
title: "Paging over SSH"
date: 2010-03-01
forum: General Help
---

### Post by johnny111 on 2010-03-01
Yesterday I tried creating and using a page-file for my laptop on my desktop with SSHFS. At first this was successful, performance was reasonable over gigabit Ethernet. The problem was (as far as I could deduce) SSHFS (which runs in user space) was paged, causing programs to freeze.

Please correct me if I'm wrong, but I predict that disallowing SSHFS to be paged will resolve this problem. If so, how could this be done?

I have read that you can protect a program's memory from paging with an edit to its source code, but I would like to avoid this if possible.

Thanks in advance.

---


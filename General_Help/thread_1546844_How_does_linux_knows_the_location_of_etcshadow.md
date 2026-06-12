---
title: "How does linux knows the location of /etc/shadow?"
date: 2010-08-05
forum: General Help
---

### Post by revered on 2010-08-05
I've being learning about how passwd and shadow file works, and I am curious about how the system knows where does files are located at, is it a var set somewhere? Can the location or name of the files be changed?

regards

---

### Post by JKyleOKC on 2010-08-06
No, they cannot be changed. "/etc/shadow" **is** the location of the file. Almost all of the system configuration files are in the /etc directory, and that directory name is hard-coded into the programs that use them (such as login).

---


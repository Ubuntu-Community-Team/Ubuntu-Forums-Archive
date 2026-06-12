---
title: "Can no longer sudo!!!"
date: 2006-03-15
forum: General Help
---

### Post by EEPS on 2006-03-15
HI, I was messing around and accidently changed the host name on my comp. Now, every time I try to sudo, it tells me that it failed to look up my host name with gethostbyname() and does not work! What does this have to do with my ability to sudo? and how can I change my host name back again without sudo?

-thanks

---

### Post by codejunkie on 2006-03-15
[QUOTE=EEPS]HI, I was messing around and accidently changed the host name on my comp. Now, every time I try to sudo, it tells me that it failed to look up my host name with gethostbyname() and does not work! What does this have to do with my ability to sudo? and how can I change my host name back again without sudo?

-thanks[/QUOTE]
get an ubuntu live cd, boot into the live cd then mount your ubuntu partition and repair your hosts file.

---

### Post by taurus on 2006-03-15
What does your /etc/hosts look like now?

---


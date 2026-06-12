---
title: "UserID mapping"
date: 2009-11-23
forum: General Help
---

### Post by karlson on 2009-11-23
Does anyone know if there are any packages that set up users with UID of 500 and above?

---

### Post by QLee on 2009-11-23
> **karlson said:**
> Does anyone know if there are any packages that set up users with UID of 500 and above?

I'm not sure I understand your question. The range for dynamically assigned user ID is set on the system, it's not done by a "package". Can you explain your question in more detail?

---

### Post by karlson on 2009-11-23
> **QLee said:**
> I'm not sure I understand your question. The range for dynamically assigned user ID is set on the system, it's not done by a "package". Can you explain your question in more detail?

I think I found the answer to my question.  The UserID that packages need are assigned dynamically vs. statically within the deb package configuration scripts.  E.g. mysql user can have different user ids between systems depending on when the package was installed in the sequence.

---


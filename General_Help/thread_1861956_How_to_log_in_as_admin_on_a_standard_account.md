---
title: "How to log in as admin on a standard account?"
date: 2011-10-16
forum: General Help
---

### Post by foxy123 on 2011-10-16
I've got admin account on my daughter's netbook, while she's got a standard account. When I need to perform any admin tasks I have to switch to my admin account. I wonder if I can log in as admin in terminal without actually going to my account?

---

### Post by mcduck on 2011-10-16
Sure you can. That's what "su" is for.

```
su yourusername
```
...and confirm with your own password.

---

### Post by foxy123 on 2011-10-16
> **mcduck said:**
> Sure you can. That's what "su" is for.

```
su yourusername
```
...and confirm with your own password.

Great! Thanks a lot for that.

---

### Post by mcduck on 2011-10-16
no problem. :)

I forgot to add that the "exit" command will log you out again when you are ready.

---


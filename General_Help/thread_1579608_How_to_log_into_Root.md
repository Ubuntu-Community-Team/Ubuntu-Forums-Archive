---
title: "How to log into Root"
date: 2010-09-22
forum: General Help
---

### Post by Poltergiest on 2010-09-22
I am having trouble logging in as Root is there a default password or do I just need to unlock the right to use it. (I'm running Ubuntu 10.04 BTW) 

Thank You

---

### Post by baddog144 on 2010-09-22
To log in as root, do
```

sudo su

```

---

### Post by mr_luksom on 2010-09-22
Logging in as root is probably not a great idea. I always thought the point of having separate user/root accounts is to prevent windows-esqe security exploits. 

Can you use sudo for what you are trying to do?

---

### Post by mcduck on 2010-09-22
> **Poltergiest said:**
> I am having trouble logging in as Root is there a default password or do I just need to unlock the right to use it. (I'm running Ubuntu 10.04 BTW) 

Thank You

Most likely you have absolutely no reason to log in as root.

Ubuntu doesn't have a root account enabled by default, instead it uses "sudo" to allow admin users temporarily root access (using their own password). There are very few situations where you might need to use actual root login instead, and if you were doing something that requires it you definitely would know how to enable root as well... ;)

Anyway, you should definitely read this: [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

If you need more help than what that article can provide, please tell us what you are trying to do so that we'll be able to give more specific answers.

---


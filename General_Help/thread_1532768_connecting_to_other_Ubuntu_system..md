---
title: "connecting to other Ubuntu system."
date: 2010-07-16
forum: General Help
---

### Post by agent_509 on 2010-07-16
I have a friend who recently set up a Ubuntu system at his house. I was wondering if there was a way to set it up so he can connect to my system remotely, while only having access to an account I made specifically for him, and so we can both use it at the same time.

---

### Post by Bradj47 on 2010-07-16
If you have it configured in your router and you have openssh-server installed on your system, he should be able to ssh to your IP address like so:

```
ssh xxx.xxx.x.xxx
```

And he should have command line access. I have never done this over the internet, but I've talked to some people who have done it with Solaris. You might also want to read the man page on **scp** for transferring files between the computers.

---

### Post by agent_509 on 2010-07-16
thanks. What do i need to do to configure it on my router? port forward?

---

### Post by prodigy_ on 2010-07-16
> **agent_509 said:**
> port forward?
Yes. SSH uses TCP port 22 by default.

---

### Post by agent_509 on 2010-07-16
okay, thanks!

---


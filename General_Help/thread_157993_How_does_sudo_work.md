---
title: "How does sudo work?"
date: 2006-04-10
forum: General Help
---

### Post by Ian Maxwell on 2006-04-10
No, this isn't the usual question.

I was actually wondering if anyone here had some insight into how sudo works internally, such that it bypasses the need for a correct root password. (This might require me to understand a bit more about how the security system itself works, so if there is something I could read on that, I'd appreciate any pointers to it.)

---

### Post by krismatth3 on 2006-04-10
I believe sudo is installed "SUID root" meaning that whenever it is executed by anyone, it is running with roots permissions.

---

### Post by frodon on 2006-04-10
This will answer your question, i hope : [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by steve.horsley on 2006-04-10
krism is right. Look at this file listing:
> steve@dingly:~$ ls -l /usr/bin/sudo
-rwsr-xr-x  1 root root 93332 2006-01-09 10:41 /usr/bin/sudo
The s in the permissions id "setuid" - it sets the user id of any process that runs it to the id of the owner - root in this case. So when you run sudo, if always runs with root permission. You only ever set the suid bit for programs that you trust absolutely, and sudo can be trusted to only allow users to do what the configuration file /etc/sudoers says they are allowed to do.

---


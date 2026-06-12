---
title: "ssh 177ELF error"
date: 2010-01-28
forum: General Help
---

### Post by daniele75 on 2010-01-28
Hello all.
On my mail server, where all works very weel, I've this problem.
SSHD is running fine and we were logging into server with root user.
Due to security policies, we have created other users to login and then perform root operation with sudo command.

But when we try to login to the server with new users, they reply with a

177ELF

error and suddenly logout.

If I insert a wrong password it reply with normal error.

Into /var/log/auth.log both error are reported as wrong password...

Any help will be greatly appreciated,

Thanks
Daniele

---

### Post by doas777 on 2010-01-28
usually (at least for me) an ELF error indicates that you are mixing 32bit and 64bit depemdencies (which most systems do not like). i am likely wrong in your case, but it is somthing to think about.

---

### Post by daniele75 on 2010-02-02
Thanks for your reply.

In my case is a 32bit installation.

Root access with ssh is working properly.

Any other idea?

Thanks
Daniele

---

### Post by daniele75 on 2010-02-10
Anyone can help me?

---


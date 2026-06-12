---
title: "ssh: connect to host 179.21.57.142 port 22: Connection refused"
date: 2009-07-10
forum: General Help
---

### Post by mrakesh85 on 2009-07-10
I am able to connect my lab system using ssh. But I am unable to connect my system from lab using ssh, the above error is coming when I tried to connect. can u tell me how to fix this problem.

---

### Post by XCan on 2009-07-10
If the sshd is running correctly on your computer, then I would guess it's a firewall issue. But you really need to provide more information.

---

### Post by e24ohm on 2009-07-10
> **mrakesh85 said:**
> I am able to connect my lab system using ssh. But I am unable to connect my system from lab using ssh, the above error is coming when I tried to connect. can u tell me how to fix this problem.

Do they have ssh on a different port? I know a number admins, including myself usually change the port ssh uses.

---

### Post by jhofmann on 2009-07-10
That's happened to me several times.  In each case, it was a new-install situation.  sshd was not installed and not running.  I had to install it with apt-get install sshd  Then configuration takes place and sshd serves incoming requests on port 22 and all is well again.

Hope this helps,
Jim

---

### Post by mrakesh85 on 2009-07-11
> **jhofmann said:**
> That's happened to me several times.  In each case, it was a new-install situation.  sshd was not installed and not running.  I had to install it with apt-get install sshd  Then configuration takes place and sshd serves incoming requests on port 22 and all is well again.

Hope this helps,
Jim

Thank you very much jim for your reply problem was solved after installing openssh-server.

Rakesh

---

### Post by mrakesh85 on 2009-07-11
Thank you very much to all,  above problem was solved after installing openssh-server.

Rakesh

---


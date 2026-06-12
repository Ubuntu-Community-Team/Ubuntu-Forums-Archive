---
title: "SSH Tunnel"
date: 2010-02-10
forum: General Help
---

### Post by Joshua Lückers on 2010-02-10
Internet at school is being protected pretty good, thats why we as IT students are allowed to tunnel trough a special server at school. Let's call this server A.
Then there is another server named B, this server is being used to commit our school projects via SVN.
At windows we make a SSH connection via putty to server A and tunnel to server B at port 8443.
How can I accomplish this under Ubuntu 9.10 so that it works system wide?

---

### Post by slakkie on 2010-02-10
ssh -L 7001:target_host:7001 target_host

---

### Post by Joshua Lückers on 2010-02-10
Where target_host is server A or B?

---

### Post by DemonStar55 on 2010-02-10
I use [http://johmanx.com/?pid=28](http://johmanx.com/?pid=28) for tunneling, python version that is.

---


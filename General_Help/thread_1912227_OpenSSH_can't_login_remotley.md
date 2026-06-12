---
title: "OpenSSH can't login remotley"
date: 2012-01-20
forum: General Help
---

### Post by hippytyre on 2012-01-20
Hello,

I run OpenSSH on my HTPC and I can access it from within my network using WinSCP without problems if I use the network ip 192.168.1.25
I have port 22 forwarded on my router to that network address but for some reason I cannot access SSH from outside my network.
I've tried changing the SSH port to a higher one(I used 6000) but this didn't seem to help either.

Do I need to alter anything else in sshd_config to make it accessible remotely? 

Thanks

---

### Post by Lars Noodén on 2012-01-20
You might check to see if your ISP is blocking your incoming connection:

[http://canyouseeme.org/](http://canyouseeme.org/)

That can sometimes be the problem.

---

### Post by hippytyre on 2012-01-20
Thanks Lars, I thought the same and checked that too. I figured out what the problem was. I'm running DD-WRT and it had a SSH server running on port 22.....

Silly mistake on my part but I have it resolved now, just changed the routers ssh port to another and then rebooted.

---


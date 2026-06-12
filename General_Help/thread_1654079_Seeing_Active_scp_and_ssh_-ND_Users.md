---
title: "Seeing Active scp and ssh -ND Users"
date: 2010-12-27
forum: General Help
---

### Post by steevven1 on 2010-12-27
I have noticed something: If I use scp to copy a large file from my ssh server, or I use ssh -ND to tunnel a port from my client through my ssh server, my connections show up in /var/log/auth.log on the server, but issuing the "w" or "who" command does not show any of the users who are transferring files via scp or using ssh -ND.

I need to know when my users are logged in (even if they're just using scp or ssh -ND) on my server so that I know when rebooting may disconnect them. The only way I know of to do this is to actually manually read /var/log/auth.log or to do "netstat -an | grep #SSHPORTNUMBER" but I don't like either of these methods. I want to be able to see (as the "w" or "who" command does for normal ssh connections) a list of all logged-in users INCLUDING those logged in using scp or ssh -ND.

Thanks in advance for any help!

---

### Post by steevven1 on 2011-01-02
Bump?

---

### Post by steevven1 on 2011-01-03
I'd really appreciate any help here, even if the answer is a definitive "you can't do that."

---


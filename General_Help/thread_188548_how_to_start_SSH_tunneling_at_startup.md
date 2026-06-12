---
title: "how to start SSH tunneling at startup?"
date: 2006-06-04
forum: General Help
---

### Post by medya on 2006-06-04
I use an SSH to connect to interent ... 
I enter this command every time I start up

ssh -L 8213:localhost:8213 root@225.244.201.149

then it asks me to enter my password (the server's password not UBUNTU's root password)


it is a bit annoying... is there any way to make ubuntu do these things for me at startup ?(connect and enter password for me automaticly)

---

### Post by medya on 2006-06-04
why nobody replies to my topics... it has been a while since nobody replies to any of my topics.
i dont know may be I ask too stupid questions,or may be ubuntu guys like to help New Commers more... (to encourage them use ubuntu)

---

### Post by Slim Odds on 2006-06-04
[quote=medya]why nobody replies to my topics... it has been a while since nobody replies to any of my topics.
i dont know may be I ask too stupid questions,or may be ubuntu guys like to help New Commers more... (to encourage them use ubuntu)[/quote] 
You could "key" based authentication. That's better anyway. I turn off username/password based authentication on systems where I'm most concerned about security, ESPECIALLY since you are using the ROOT account.

Take a quick peek at the documentation for sshd.

---

### Post by bjc on 2006-06-04
Take a look at [http://www.debian-administration.org/articles/152](http://www.debian-administration.org/articles/152) for practical instructions.

---


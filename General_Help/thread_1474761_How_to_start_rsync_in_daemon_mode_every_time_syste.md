---
title: "How to start rsync in daemon mode every time system turns on"
date: 2010-05-06
forum: General Help
---

### Post by DaF1oh1 on 2010-05-06
Hey guys,

I have a Linux box, running rsync, only problem is, I have to turn it off at night. What I want to do is turn it on and when it turns on, rsync will already be running in daemon mode rather then having to run rsync --daemon. Does anyone know the solution? I'm sure its simple, I just cannot figure it out

---

### Post by HermanAB on 2010-05-06
I have never used the rsync daemon, since it is not secure.  It is better to run rsync over ssh using the sshd daemon.  See the man page.  The command is basically rsync -e ssh yadda yadda

---

### Post by DaF1oh1 on 2010-05-07
I'm just running this over my network at home, this isn't over the net or anything, otherwise I would do it over SSH, The reason why I want to do this is because I want to make it automated from my home PC using a password file in clear text, yeah insecure, but its running at home not corporate

---

### Post by StuartN on 2010-05-07
> **DaF1oh1 said:**
> when it turns on, rsync will already be running in daemon mode rather then having to run rsync --daemon.

Edit /etc/default/rsync to contain RSYNC_ENABLE=true.

---


---
title: "SSH port forwarding"
date: 2010-11-03
forum: General Help
---

### Post by venicequeen7706 on 2010-11-03
I have open ssh on my computer and i'm trying to use it to use local port forwarding to get around my school's firewall to use youtube for a presentation. I typed 'ssh -L 8080:[www.youtube.com:80](www.youtube.com:80) chris-laptop' and used firefox to look to  [http://localhost:8080/](http://localhost:8080/) and I ended up at google.com. confused, I tried to ssh to another site to see what was going wrong. I typed 'ssh -L 8080:[www.xkcd.com:80](www.xkcd.com:80) chris-laptop' the used firefox to go to [http://localhost:8080/](http://localhost:8080/) and got the website, but it loaded strangely and without the images that were supposed to be on it. Any explanation of what i'm doing wrong?

---

### Post by Soul-Sing on 2010-11-03
Open ssh runs by default via port 22
take a look here: [http://www.debuntu.org/2006/04/08/22-ssh-and-port-forwarding-or-how-to-get-through-a-firewall](http://www.debuntu.org/2006/04/08/22-ssh-and-port-forwarding-or-how-to-get-through-a-firewall)
: [https://help.ubuntu.com/community/SSH/OpenSSH/Configuring](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring)

---

### Post by venicequeen7706 on 2010-11-03
I read those and I don't see anything that helps. also, I tried the same process to get to facebook, which is also blocked, and that worked perfectly, facebook came up normally. any other ideas?

---

### Post by SlugSlug on 2010-11-03
[http://ubuntuforums.org/showthread.php?t=723025](http://ubuntuforums.org/showthread.php?t=723025)

---

### Post by venicequeen7706 on 2010-11-03
Thanks but that isn't helping anything

---

### Post by CharlesA on 2010-11-03
We don't support bypassing firewalls here. Closed.

---


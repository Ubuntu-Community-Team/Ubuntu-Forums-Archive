---
title: "Dangers of running a server"
date: 2010-01-16
forum: General Help
---

### Post by eggbloke on 2010-01-16
I have an old laptop (running Xubuntu 8.04 and apache) which i use as a webserver, and have opened port 88 on my router. Is this a danger to other computers on my network?

---

### Post by bsh on 2010-01-16
yes

---

### Post by john newbuntu on 2010-01-16
Isolation of webserver with other servers is a good idea

---

### Post by eggbloke on 2010-01-16
Thanks John. How might I go about doing that?

---

### Post by john newbuntu on 2010-01-17
Hi eggbloke.  I am not a web admin myself but have worked in a web service company.  I guess what I was meaning was that if the development machines are open to the internet and have vulnerabilities and if these machines can talk to production ones, then you have pretty much compromised your production data.  This is what I meant by isolating the 2 environments.  Perhaps this only matters if you carry critical data.

As far as other ways to protect your server, I am sure there's tons of stuff on the internet that will give you more info.

---

### Post by eggbloke on 2010-01-17
I just dont want the windows computers on my network getting infected, is there a way to allow the server to access the internet but not any other computers on my LAN?

---


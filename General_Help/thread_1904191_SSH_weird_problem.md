---
title: "SSH weird problem"
date: 2012-01-04
forum: General Help
---

### Post by acastrolorenzo on 2012-01-04
Hi,

I've installed a Ubuntu 10.10 server edition, did the SSH intallation and so. I connect it via
ssh root@myip last night and everything was ok. But now I tried again and get a weird error "no route to host".

Any idea?,
Thanks in advance

---

### Post by sj1410 on 2012-01-04
first check if you are able to ping your server. if yes than check if the ssh service is running by

```

service ssh status

```

---


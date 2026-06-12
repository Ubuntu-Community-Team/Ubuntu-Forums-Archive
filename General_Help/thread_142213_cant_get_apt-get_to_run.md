---
title: "cant get apt-get to run"
date: 2006-03-10
forum: General Help
---

### Post by jeisma on 2006-03-10
hi!

```

~/.bashrc 

http_proxy=http://192.168.0.2:8088
export http_proxy

```

```

/etc/apt/apt/conf

Acquire
{
http::proxy "http://192.168.0.2:8088"
}

```

```

/etc/bash.bashrc

export http_proxy=http://192.168.0.2:8088/
export ftp_proxy=http://192.168.0.2:8088/

```

having the above entries in the mentioned config files, i still cant get apt-get to run. always gets "403 forbidden" when i try to run apt-get update.

help pls?

thank you!

---

### Post by dmizer on 2006-03-10
in ubuntu, you need to prefix apt-get with sudo ... so:

sudo apt-get update.

if you've already done that, my apologies.

---


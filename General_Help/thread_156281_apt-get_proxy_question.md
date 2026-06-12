---
title: "apt-get proxy question"
date: 2006-04-06
forum: General Help
---

### Post by yellow beard on 2006-04-06
*SLOVED*

ive configured apt with 

```

ACQUIRE {
http::proxy "http://192.168.253.1:8080/"
}

```

apt connects but it cant download anything because my server requires that i log in. how do i add my user name/password so apt-get update will work?

---

### Post by ape on 2006-04-07
From the apt.conf manpage:

  ```
HTTP URIs; http::Proxy is the default http proxy to use.  It  is
    in the standard form of [http://[](http://[)[user][:pass]@]host[:port]/.
```

---


---
title: "External machines can see SOME subdomains but not all"
date: 2010-09-16
forum: General Help
---

### Post by JasonSwett on 2010-09-16
I have a DNS server on my LAN at 192.168.140.25. Going by the example in the O'Reilly DNS and BIND book I bought, I set up the domain movie.edu and toystory.movie.edu.

To my great surprise and delight, I can access toystory.movie.edu in a browser from another PC on the LAN (as long as I add 192.168.140.25 to the DNS servers). Encouraged by this victory, I decided to try to set up another subdomain at coupon.movie.edu.

This kind of worked but not completely. Interestingly, I can get to both toystory.movie.edu and coupon.movie.edu on my server, but on my PC, I can only get to toystory.movie.edu, not coupon.movie.edu.

Here is my db.movie.edu:
```

$TTL 3h

movie.edu. IN SOA toystory.movie.edu. al.movie.edu. (
  1        ; Serial
  3h       ; Refresh after 3 hours
  1h       ; Retry after 1 hour
  1w       ; Expire after 1 week
  1h )     ; Negative caching TTL of 1 hour

movie.edu.  IN NS  toystory.movie.edu.
movie.edu.  IN NS  coupon.movie.edu.

;
; Host addresses
;
localhost.movie.edu.      IN A   127.0.0.1
toystory.movie.edu.       IN A   192.168.140.25
coupon.movie.edu.         IN A   192.168.140.25

```

And here is my named.conf:

```

options {
  directory "/etc/bind";
};

zone "movie.edu" in {
  type master;
  file "db.movie.edu";
};

zone "140.168.192.in-addr.arpa" in {
  type master;
  file "db.192.168.140";
};

zone "0.0.127.in-addr.arpa" in {
  type master;
  file "db.127.0.0";
};

zone "." in {
  type hint;
  file "db.cache";
};

#include "/etc/bind/named.conf.options";
include "/etc/bind/named.conf.local";
#include "/etc/bind/named.conf.default-zones";

```

Any ideas?

Thanks,
Jason

---

### Post by JasonSwett on 2010-09-16
Scratch that: now I can't see either subdomain on my PC.

---

### Post by JasonSwett on 2010-09-16
Restarted the PC on a whim and now it works.

---


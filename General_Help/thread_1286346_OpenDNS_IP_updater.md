---
title: "OpenDNS IP updater"
date: 2009-10-08
forum: General Help
---

### Post by jasonmh on 2009-10-08
I found this script which is supposed to update my dynamic IP with the OpenDNS filter, however it keeps failing on the &gt;&gt;  Does anyone know why?

```
[SIZE="2"]
date &gt;&gt; ~/.opendns/log
/usr/bin/curl -i -m 60 -k -u username:password 'https://updates.opendns.com/account/ddns.php?' -silent &gt;&gt; ~/.opendns/log
echo -e "\n" &gt;&gt; ~/.opendns/log
[/SIZE]
```

---

### Post by nooblot on 2009-10-11
> **jasonmh said:**
> I found this script which is supposed to update my dynamic IP with the OpenDNS filter, however it keeps failing on the &gt;&gt;  Does anyone know why?

```
[SIZE="2"]
date &gt;&gt; ~/.opendns/log
/usr/bin/curl -i -m 60 -k -u username:password 'https://updates.opendns.com/account/ddns.php?' -silent &gt;&gt; ~/.opendns/log
echo -e "\n" &gt;&gt; ~/.opendns/log
[/SIZE]
```

You copied bad code (">" got converted to "&gt;")

```

date >> ~/.opendns/log
/usr/bin/curl -i -m 60 -k -u username:password 'https://updates.opendns.com/account/ddns.php?' -silent >> ~/.opendns/log
echo -e "\n" >> ~/.opendns/log

```

[also look here for your reference]("http://bassmadrigal.com/blog/?p=7")

---


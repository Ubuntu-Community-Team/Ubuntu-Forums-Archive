---
title: "/usr/share/doc/shorewall-common/default-config no such directory"
date: 2010-07-12
forum: General Help
---

### Post by rock_rebel on 2010-07-12
Hi,

I'm trying to set up Shorewall to work with my mail server. I've installed shorewall, shorewall-common, shorewall-doc, and shorewall-perl. When I try to set up my network interface using the info found in the default-config folder, I get this error message:

/usr/share/doc/shorewall-common/default-config no such file or directory

When I go to the shorewall-common folder there's just a bunch of change logs and release notes, nothing in regard to configuring the firewall.

The /etc/shorewall folder does exist, and contains shorewall.conf. I'm not sure how to proceed further with this file however.

Could it be something I've done wrong? I tried re-installing everything mentioned above, but still no luck. Thanks for your help.

---

### Post by rock_rebel on 2010-07-13
Bump

---

### Post by Andreauk on 2010-07-22
Try:

```
/usr/share/doc/shorewall/default-config/
```

---

### Post by pligor on 2011-03-19
fixed
thanks! this whole deal with the rearrangement of folders is troublesome

---


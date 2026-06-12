---
title: "Apache service - incorrect messages and behaviour"
date: 2011-11-17
forum: General Help
---

### Post by HotForLinux on 2011-11-17
In Hardy (and probably other releases too):

a) Upgrading Apache's packages often starts the service when the service was not running and it is marked as off in services-admin.

b) Consulting the status of the service and trying to stop it, as a normal user with
/etc/init.d/apache2  start / stop
without sudoing the command, gives erroneous/misleading messages.

Are these things still happening in new versions?
Are they ok? , are they intended? I don't understand their reason.

---


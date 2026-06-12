---
title: "Proxy Configuration"
date: 2010-09-14
forum: General Help
---

### Post by bravo13 on 2010-09-14
Hi All,
             How can we force an application which is using a direct Internet connection inherently to connect through a proxy server connection. Like redirecting the direct traffic generated to a proxy server.


Thanks in advance.

---

### Post by sikander3786 on 2010-09-14
Which specific program are you talking about? If you've got a direct internet connection as well as a proxy enabled on the same network, you will have to configure proxy in the program's connection settings.

For system wide proxy settings go to System >>> Preferences >>> Network Proxy.

---

### Post by bravo13 on 2010-09-14
A custom application which needs direct connection to internet, which does not support a proxy configuration.

---

### Post by sikander3786 on 2010-09-14
Can you provide a link to that application? Doesn't it follow the system wide proxy configuration of GNOME?

---

### Post by bravo13 on 2010-09-14
Empathy Instant Messenger does not support proxy configuration

---

### Post by sikander3786 on 2010-09-14
Seems to be a bug.

[https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/304889](https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/304889)

Revert to Pidgin if it isn't sorted out.

You can also try some proxifier like tsocks.

---


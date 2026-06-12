---
title: "lighttpd &quot;No configuration available. Try using -f option&quot;"
date: 2010-06-29
forum: General Help
---

### Post by walterbyrd on 2010-06-29
I can not get lighttpd to work correctly. I keep getting the error:

> lighttpd "No configuration available. Try using -f option"

---

### Post by justleen on 2010-06-29
It can't find any config..
The -f option allows to specify a config file if it is not in the default directory.
Default is /etc/lighttpd/lighttpd.conf

non-default would be  /usr/sbin/lighttpd -f /path/to/config/lighttpd.conf


Check /usr/share/doc/lighttpd/examples for example configs.

---

### Post by walterbyrd on 2010-06-29
I know where the config file exists. But, why does it constantly need me to force reload that file? How do I set this up to load the config file the way it is supposed to do?

---

### Post by justleen on 2010-06-30
Perhaps you should explain a bit more?

How and when do you get this error?

---


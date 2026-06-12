---
title: "cannot find bootmisc.sh in Ubuntu 10.10"
date: 2011-02-14
forum: General Help
---

### Post by yushengc on 2011-02-14
I would like to edit the welcome message after logging in. 

I searched relative solutions, results showed that to prevent from being refreshed by default text after rebooting, /etc/motd.tail and  /etc/init.d/bootmisc.sh should be edited. However, I could not find them under the Ubuntu 10.10. 

Any suggestion?

---

### Post by gmargo on 2011-02-14
If you want a static message, change the /etc/motd symbolic link to point to a file such as /etc/motd.static.  If you want a custom message following the automatically generated part, then create /etc/motd.tail.

It does seem that the **motd.tail(5)** documentation is out of date.  The generated motd file is created by the **upstart(8 )** system from /etc/init/mounted-varrun.conf (but you should not be editing that script.)

---


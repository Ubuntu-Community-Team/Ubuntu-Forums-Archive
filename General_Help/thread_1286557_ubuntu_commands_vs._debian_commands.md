---
title: "ubuntu commands vs. debian commands"
date: 2009-10-09
forum: General Help
---

### Post by kpholmes on 2009-10-09
since ubuntu is based of debian, then are all the commands the same, like apt-get?

obviously i dont expect the respitories to be the same, but can i take my knowledge that i have learned in ubuntu and apply it to a Debian server easily?

---

### Post by jaxxstorm on 2009-10-09
> **kpholmes said:**
> since ubuntu is based of debian, then are all the commands the same, like apt-get?

obviously i dont expect the respitories to be the same, but can i take my knowledge that i have learned in ubuntu and apply it to a Debian server easily?

More or less, yes.

In fact, most Linux commands are the same. The differences is in package manager and location of some configuration files.

If you know where something is in Ubuntu (such as /etc/casper.conf for example) its easy enough to locate it in another distro using a combination of find, grep, locate and whereis commands.

---


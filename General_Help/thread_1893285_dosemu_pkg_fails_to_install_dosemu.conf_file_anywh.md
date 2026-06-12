---
title: "dosemu pkg fails to install dosemu.conf file anywhere"
date: 2011-12-09
forum: General Help
---

### Post by ralvy on 2011-12-09
I find that after installing dosemu from the ubuntu 11 repos, it never installs dosemu.conf anywhere. It's sure not in the usual place, which would be the target as seen in the install pkg. I also did an updatedb, followed by a locate for that file, and it doesn't exist. I have uninstalled and reinstalled the pkg, to no avail.

Any ideas?

---

### Post by jerrrys on 2011-12-11
should be /etc/dosemu/dosemu.conf

---

### Post by ralvy on 2011-12-11
Yes. That's where it's supposed to be, but it's not there. Very odd.

---

### Post by jerrrys on 2011-12-11
Yes, odd indeed.  Are the other /dosemu files there?

---

### Post by ralvy on 2011-12-11
The only files in /etc/dosemu are my drives and freedos folders. I can't find a dosemu.conf file anywhere on the hard drive. dosemu runs fine. I just wanted to speed it up a little by increasing its hogthreshold value. I can always grab a copy of the latest dosemu.conf file from within the package, or grab it from another installed distro. I just thought this was very odd.

---

### Post by jerrrys on 2011-12-11
should be more than that

[ATTACH]208903[/ATTACH]

---


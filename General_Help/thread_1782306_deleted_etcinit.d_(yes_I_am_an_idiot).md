---
title: "deleted /etc/init.d/ (yes I am an idiot)"
date: 2011-06-14
forum: General Help
---

### Post by jony121 on 2011-06-14
I accidentally deleted /etc/init.d/

I was having trouble removing a script. I decided just to rm the sucker and poof, before I could finish the line I had accidentally pressed return. :(

initscripts won't re-install.

Could someone running 11.04 (don't think it has to be 64bit) please make a tarball of their /etc/init.d/ and send it to me please.

---

### Post by FormatSeize on 2011-06-14
If you have the live cd you can copy it from there.

---

### Post by jony121 on 2011-06-14
Excellent idea! :D

---

### Post by sisco311 on 2011-06-14
The following commands should reinstall all packages which have files in /etc/init.d:
```

sudo apt-get update
sudo apt-get --reinstall install $(dpkg -S /etc/init.d/ | sed -e 's_,__g' -e 's_: /etc/init.d$__')
```

---

### Post by jony121 on 2011-06-14
All fixed now! :D Thanks very much guys.

---


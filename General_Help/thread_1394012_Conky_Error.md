---
title: "Conky Error"
date: 2010-01-30
forum: General Help
---

### Post by TCKChris on 2010-01-30
sempo@ubuntu-desktop:~$ conky
Conky: got an else without matching if
Conky: X Error: type 0 Display d9fc30 XID 0 serial 23 error_code 3 request_code 61 minor_code 0 other Display: d9fc30

Aborted (core dumped)

---

### Post by Johnny B on 2010-01-30
you need to tell conky what file to open:
$ conky -c /path-to-file

---

### Post by josepaul on 2010-02-09
> **Johnny B said:**
> you need to tell conky what file to open:
$ conky -c /path-to-file

Hi, I have this same problem, the path to what file are you talking about?

---

### Post by daFlo on 2010-02-24
I also had an xerror but with another error_code... for me the newest version of conky helped.

[https://launchpad.net/~norsetto/+archive/ppa/+sourcepub/941558/+listing-archive-extra](https://launchpad.net/~norsetto/+archive/ppa/+sourcepub/941558/+listing-archive-extra)

---

### Post by cong06 on 2010-02-24
I might not know what I'm talking about, but it sounds like your  ~/.conkyrc file is screwed up.
post it and see what we can do.

---


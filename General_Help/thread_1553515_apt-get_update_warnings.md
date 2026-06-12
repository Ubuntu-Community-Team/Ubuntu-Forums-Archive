---
title: "apt-get update warnings"
date: 2010-08-15
forum: General Help
---

### Post by bprins on 2010-08-15
Hi,

how can i get rid of the following warnings:
```

W: Duplicate sources.list entry http://security.ubuntu.com/ubuntu/ lucid-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_lucid-security_main_binary-i386_Packages)
W: Duplicate sources.list entry http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_lucid-security_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry http://security.ubuntu.com/ubuntu/ lucid-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_lucid-security_restricted_binary-i386_Packages)


```

can i just delete those duplicates from /etc/apt/sources.list?

why does apt allow duplicates entries to begin with? shouldn't it have warned me when I was about to add lines to its database that already exist?

thanks in advance.

bas

---

### Post by howefield on 2010-08-15
Yes, you can edit sources.list and remove the offending lines or comment them out.

---

### Post by Smart Viking on 2010-08-15
Yes you can safely remove dublicates. :)

---

### Post by bprins on 2010-08-15
alright, thanks.

Bas

---


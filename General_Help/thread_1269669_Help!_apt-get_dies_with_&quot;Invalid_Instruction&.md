---
title: "Help! apt-get dies with &quot;Invalid Instruction&quot; error"
date: 2009-09-18
forum: General Help
---

### Post by monkeyBox on 2009-09-18
```

ben@ben-laptop ~ $ sudo apt-get update

Get:1 http://security.ubuntu.com jaunty-security Release.gpg [189B]
Ign http://security.ubuntu.com jaunty-security/main Translation-en_US
(...snip...)
Get:17 http://us.archive.ubuntu.com jaunty-updates/universe Packages [55.6kB]
Get:18 http://us.archive.ubuntu.com jaunty-updates/universe Sources [14.9kB]
Get:19 http://us.archive.ubuntu.com jaunty-updates/multiverse Packages [8128B]
Get:20 http://us.archive.ubuntu.com jaunty-updates/multiverse Sources [2505B]
Fetched 574kB in 2s (239kB/s)  
Getting package lists... 0%
Illegal instruction
```

Also when I run apt-cache search, I just get the "Illegal instruction" error.

What is causing this?

---


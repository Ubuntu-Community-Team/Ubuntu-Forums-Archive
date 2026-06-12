---
title: "Dependencies problem"
date: 2011-11-03
forum: General Help
---

### Post by gdiazc on 2011-11-03
Hello!

I need help with aptitude:

```
sudo apititude install libaprutil1-dev
```

gives me the following error:

```

The following packages have unmet dependencies:
  libapr1-dev: Depends: libapr1 (= 1.4.2-7ubuntu2.1) but 1.4.5-1 is installed.
  libaprutil1-dev: Depends: libaprutil1 (= 1.3.9+dfsg-5ubuntu3) but 1.3.12+dfsg-2 is installed.
  uuid-dev: Depends: libuuid1 (= 2.17.2-9.1ubuntu4) but 2.19.1-5 is installed.
The following actions will resolve these dependencies:

     Keep the following packages at their current version:
1)     libapr1-dev [Not Installed]                        
2)     libaprutil1-dev [Not Installed]                    
3)     uuid-dev [Not Installed]

```

Can anyone help me? Thanks!

---

### Post by community on 2011-11-04
Try to install the packages quoted in the error list first.Then install the required package.If not working stay updated with the errors..

---


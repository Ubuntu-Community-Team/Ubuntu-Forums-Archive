---
title: "please help me"
date: 2010-02-24
forum: General Help
---

### Post by Shawn1991 on 2010-02-24
I am in school and we are learning about ubuntu. our server for the classroom is run by windows. how do i connect to that server? in the places/network folder it has my server listed but doesnt show anything in it. im totally lost. any help?

---

### Post by jamesisin on 2010-02-24
Ubuntu (and other distributions) uses Samba to emulate Windows Share environments.  In most cases you will be able to connect to a Windows share using this syntax:

```
smb://server/share
```

You can find a lot of information about using Samba here:

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

---


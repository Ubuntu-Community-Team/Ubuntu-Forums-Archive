---
title: "Ok we are going to AIX and Korn Shell"
date: 2011-06-10
forum: General Help
---

### Post by Deaf Smith on 2011-06-10
For our companies new system. 15 servers!
 
Now is there any way to get the Korn shell, or something that mimics it, on a Ubuntu system so I can practice? 
 
I have the desktop 10.1 version at home and the server 10.04 on my test PC.
 
Thanks for any help.

---

### Post by tredegar on 2011-06-10
Install **ksh** or **pdksh**

---

### Post by gmargo on 2011-06-10
```

$ apt-cache search korn | grep Korn | sort
ksh - The real, AT&T version of the Korn shell
mksh - MirBSD Korn Shell
pdksh - A public domain version of the Korn shell

```

---


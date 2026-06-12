---
title: "Compiling Glest"
date: 2009-08-07
forum: General Help
---

### Post by AxelMan0 on 2009-08-07
I wanted to try version 3.2.2 and I'm fairly sure I have all the dependencies. When I go to run ./autogen.sh the terminal tells me "Permission denied" but when i run it with sudo it tells me "sudo: ./autogen.sh: command not found". autogen.sh IS a file I'm staring at it in nautilus as I type this.

---

### Post by michy99 on 2009-08-07
Have you made it executable?```
chmod a+x autogen.sh
./autogen.sh
```

---

### Post by Bonster on 2009-08-07
[http://www.getdeb.net/app/Glest](http://www.getdeb.net/app/Glest)

---

### Post by AxelMan0 on 2009-08-08
I just downloaded the .exe and ran it through wine. If I ever have to reinstall it I'll try the chmod command though. It's odd I've never had to do that with an autogen file before but oh well. Hopefully it will end up in the 9.10 repositories anyway (posting from 9.10 alpha 3 :D).

---


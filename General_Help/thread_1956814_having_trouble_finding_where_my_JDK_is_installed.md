---
title: "having trouble finding where my JDK is installed"
date: 2012-04-11
forum: General Help
---

### Post by lemonoid on 2012-04-11
I'm on 11.10 so I had to install the JDK through a ppa a month or so ago, and now I can't find where its installed. I have to create some links and I'm not having any luck finding where it is installed. I found where the jre is installed in /usr/lib/jvm but I really need to find the JDK, for some reason its not with the rest of the java files. can anyone point me in the direction of a solution? thanks in advance

---

### Post by jonobr on 2012-04-11
Hello


You can find installed programs using the which command in terminal.

eg

```
which jvm
```

Question though is which which finds jdk

Im thinking , looking at other sites it may be 
which oracle-javax-installer

x being the version number.

It should show a location

---


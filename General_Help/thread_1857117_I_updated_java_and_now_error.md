---
title: "I updated java and now error"
date: 2011-10-09
forum: General Help
---

### Post by Rent_A_Pig on 2011-10-09
[http://paste.ubuntu.com/705065/](http://paste.ubuntu.com/705065/)            

Can anyone help?

---

### Post by mikejonesey on 2011-10-09
i use java alot at work, i have mutliple jdks (jre's with) so i can play with them all... (some apps require a certain jre...). To do the same download and install extra jdk's from oracle (no longer sun...) and add alternatives for example like;

```
update-alternatives --install `which java` java /usr/lib/sun/jdk...(your path here...)
```

this will allow you to switch to diff ones easily...

---

### Post by Rent_A_Pig on 2011-10-09
how do I know what path to use?

---

### Post by mikejonesey on 2011-10-09
which java tells you the install path of current, from mem /usr/bin/java but which will take care of that, you can extract the new jdk or jre to any dir, I folled the arch for the openjre which was something like /usr/lib/openjre/... (so mine looks a bit like)...

/usr/lib/sun/jdk1.5_22/
/usr/lib/sun/jdk1.5_24/
/usr/lib/sun/jdk1.6_01/

and so on...

---


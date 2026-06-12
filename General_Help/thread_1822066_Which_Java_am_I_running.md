---
title: "Which Java am I running?"
date: 2011-08-10
forum: General Help
---

### Post by ferulebezel on 2011-08-10
I believe that I correctly installed Sun Java yet look at this.

```
foo@bar:~$ java -version
java version "1.6.0_26"
Java(TM) SE Runtime Environment (build 1.6.0_26-b03)
Java HotSpot(TM) Server VM (build 20.1-b02, mixed mode)
foo@bar:~$ javac -version
javac 1.6.0_26
```

They don't specify if it is the open one or Sun.  If it is not Sun, do I just delete the open version or what?

---

### Post by beew on 2011-08-10
Sun

---

### Post by deathadder on 2011-08-10
If you were running the OpenJDK you'd see this instead:
```

adamj@adamj-ubuntu:~$ java -version
java version "1.6.0_22"
OpenJDK Runtime Environment (IcedTea6 1.10.2) (6b22-1.10.2-0ubuntu1~11.04.1)
OpenJDK Server VM (build 20.0-b11, mixed mode)
adamj@adamj-ubuntu:~$ javac -version
javac 1.6.0_22

```

---


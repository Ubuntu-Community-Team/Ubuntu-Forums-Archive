---
title: "Java consuming resources 10.10 - 64bit"
date: 2010-12-23
forum: General Help
---

### Post by bvt on 2010-12-23
Hi, After I reboot, my java process consumes 100% of the CPU then settles down to about 40% CPU and 12% memory, status sleeping (4 core AMD)  I've removed the OpenJDK and installed Sun JRE but no difference.  by comparison, Firefox with a lot of tabs is at 3% CPU and 5% memory.

Is it better if I go to 10.04 LTS, 32 bit?

thank you,
Barry

---

### Post by lazlo on 2011-04-12
I have a very similar problem:

When I'm on a page with a Java Applet the Java JVM process eats up all available memory and even after closing the browser window the applet resided in the java process is not closed and continues to consume memory and cpu in ways that even stop the mouse from working.

I'm running Ubuntu 10.10 on x86_64

output from running "java -version":

```
java version "1.6.0_20"
OpenJDK Runtime Environment (IcedTea6 1.9.7) (6b20-1.9.7-0ubuntu1)
OpenJDK 64-Bit Server VM (build 19.0-b09, mixed mode)
```

---

### Post by lazlo on 2011-04-12
Well ... I removed OpenJDK and installed Suns Java .. problem gone.

Output of current "java -version":

```

java version "1.6.0_24"
Java(TM) SE Runtime Environment (build 1.6.0_24-b07)
Java HotSpot(TM) 64-Bit Server VM (build 19.1-b02, mixed mode)
```

---

### Post by lazlo on 2011-04-12
Okay ... problem only partially gone. The java process is now closed when the browser window with the applet is closed but the memory/cpu consumption issue is still there ... might also be related to the applet itself.

---


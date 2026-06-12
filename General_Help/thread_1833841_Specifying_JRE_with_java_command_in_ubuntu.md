---
title: "Specifying JRE with java command in ubuntu"
date: 2011-08-26
forum: General Help
---

### Post by overtone on 2011-08-26
So this ones pretty straightforward. 

I have both open jre and sun jre on this machine. 

When im calling a java command from the terminal, how do i specify which one to use?

eg java -jar executablejar.jar would run the jar file with open JDK.

---

### Post by hasardeur on 2011-08-26
Try:

```
sudo update-alternatives --config java
```

Here is a very good reference:

[http://ubuntuforums.org/showthread.php?t=1517979]("http://ubuntuforums.org/showthread.php?t=1517979")

---


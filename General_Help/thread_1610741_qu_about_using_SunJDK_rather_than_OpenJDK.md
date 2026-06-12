---
title: "qu about using SunJDK rather than OpenJDK"
date: 2010-11-01
forum: General Help
---

### Post by mrodent on 2010-11-01
- I have chosen the Sun JRE rather than the OpenJDK JRE
> sudo update-java-alternatives -v -s java-6-sun
- but how does the javac binary belonging to the Sun JDK get chosen when compiling code? Presumably there are two such files, one belonging to OpenJDK, the other to Sun JDK...?
- so how does the OS know which one to use (and where are they kept, by the way)? Is this determined by some sort of environment variable, and is the latter set when you run
> sudo update-java-alternatives -v -s java-6-sun
?

---


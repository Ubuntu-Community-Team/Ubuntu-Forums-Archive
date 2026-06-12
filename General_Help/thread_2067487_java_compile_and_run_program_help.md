---
title: "java compile and run program help"
date: 2012-10-06
forum: General Help
---

### Post by COKEDUDE on 2012-10-06
What is the trick to get a java program to run and compile? I can't even get a basic skeleton to run and compile. What packages do I need? I figured the java-gcj and gcc-java packages was enough. Do I need any other packages?

I thought I had to do this and it would work but its not.

```
javac square.java
java square
```

---

### Post by raja.genupula on 2012-10-06
```
sudo add-apt-repository ppa:webupd8team/java
  sudo apt-get update
  sudo apt-get install oracle-java7-installer

```

paste those commands one-by-one in your terminal

---


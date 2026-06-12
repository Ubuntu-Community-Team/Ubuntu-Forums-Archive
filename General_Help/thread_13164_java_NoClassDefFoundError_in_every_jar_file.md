---
title: "java: NoClassDefFoundError in every jar file"
date: 2005-01-29
forum: General Help
---

### Post by largo on 2005-01-29
Hi,
I was trying to run a jar file with the command "java blah.jar
this is what i get:
```
sevi@blue:~ $ java /home/sevi/ipod/lib/mypod.jar
Exception in thread "main" java.lang.NoClassDefFoundError: /home/sevi/ipod/lib/mypod/jar
``` 
I installed jre exactly the way it is described on ubuntuguide.org
What could have gone wrong?

---

### Post by DJ_Max on 2005-01-29
Don't think it's a problem with Java, rather your java classes. What do you have in the jar file?

---

### Post by piedamaro on 2005-01-29
try:
java -jar /home/sevi/ipod/lib/mypod.jar

(java -help to see the other options)

---

### Post by largo on 2005-01-29
This is a Ipod management programm from sourceforge. java -jar mypod.jar didnt work either. But the package should be fine, since its an official release from sourceforge. ```
sevi@blue:~/ipod/lib $ java -jar mypod.jar
Failed to load Main-Class manifest attribute from
mypod.jar
```

---

### Post by piedamaro on 2005-01-30
The first thing on mypod documentation page is that you have to run a script myPod.sh to launch the program (same as many other java apps). Did you even bother to read how to start the program on their docs?

---


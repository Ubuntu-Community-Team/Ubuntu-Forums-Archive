---
title: "Launcher not working"
date: 2010-08-19
forum: General Help
---

### Post by uttam2707 on 2010-08-19
I downloaded and unzipped the Jmol mlecuar viewer. It is a standalone application. To run the application one have to open the Jmol.jar file in it with the following command:

$ java -jar ~/<path to the directory>/Jmol.jar
$ java -jar ~/jmol\-12\.1\.5/Jmol.jar     (in my case)

The command is working fine when executed in terminal. But, in the application launcher it is not working. If the "Application in Terminal" option is chosen in the type field, upon clicking the launcher the terminal pops up for a flicker of a second and nothing happens.

---

### Post by Vaphell on 2010-08-19
try
```
sh -c "java -jar ~/jmol\-12\.1\.5/Jmol.jar; read a"
```
to see if it shows something interesting in spawned terminal

---

### Post by uttam2707 on 2010-08-21
> **Vaphell said:**
> try
```
sh -c "java -jar ~/jmol\-12\.1\.5/Jmol.jar; read a"
```
to see if it shows something interesting in spawned terminal
Thanks it worked. Can you please explain me the code?

---


---
title: "Running a .bat file"
date: 2010-11-27
forum: General Help
---

### Post by Strausss on 2010-11-27
I was wondering if it is possible to run a .bat file on Ubuntu.

Here's the codes from the two files.

Compile.bat:
```
@echo off
"C:\Program Files (x86)\Java\jdk1.6.0_18\bin\javac.exe" *.java
pause
```

run.bat
```
@echo off
cls
echo Voule Auto restart
tskill java /a
echo Restarting server
title EvolutionX RunServer
java -Xmx512m -cp .;./jython.jar;./MySql/mysql-connector-java-3.0.17-ga-bin.jar server
cls
```

---

### Post by Chronon on 2010-11-27
In general, no you can't.  However, in many cases, if you know what the batch file does it should be fairly straightforward to craft a bash script that does the same thing (like compile java source into bytecode as Compile.bat does).

---

### Post by Strausss on 2010-11-27
Mind helping me with that?

EDIT: I managed to get the .sh file, but when I choose to run it in a terminal, a terminal doesn't open.

---

### Post by Strausss on 2010-11-28
BUMP, please help me somebody.

---


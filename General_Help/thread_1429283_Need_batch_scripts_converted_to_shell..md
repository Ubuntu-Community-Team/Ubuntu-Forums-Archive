---
title: "Need batch scripts converted to shell."
date: 2010-03-13
forum: General Help
---

### Post by kciN drowkcaB on 2010-03-13
I recently installed Ubuntu 9.10 and am loving it, however I have not been able to run a couple of my java programs because they use a batch file to initialize. I did some research and figured out that the equivalent to batch on Ubuntu is a shell script, however I am to lazy to learn how to use it and create my own script. :redface:

So if someone could convert these two batch files to shell, it would be greatly appreciated. I think I could also learn how basic shell works by looking at the file.

```
@echo off 
title Server Project:Initialize 
java -Xmx512m -cp bin;libs/xstream.jar;libs/xpp.jar com.rs2.Main 43594 
pause
``````
@ECHO OFF 
SET dist=data\Program.jar
 
IF NOT EXIST "%dist%" CALL Compile.bat 
 
START /BELOWNORMAL javaw -jar -Xmx512m "%dist%" 
```

---


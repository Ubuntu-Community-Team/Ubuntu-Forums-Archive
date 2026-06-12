---
title: "How do i run this .bat file?"
date: 2010-05-25
forum: General Help
---

### Post by kommunisti on 2010-05-25
I know i can only run batch files under windows but is there any way to run this script under ubuntu?

```
@ECHO OFF 
 
TITLE RSBot Scripts 
 
SET cc=javac 
SET cflags= 
SET scripts=Scripts 
SET scriptspre=%scripts%\Precompiled 
SET jarpathfile=Settings\path.txt 
 
IF NOT EXIST "%jarpathfile%" ( 
    ECHO Path file does not exist. Please run RSBot and try again. 
    GOTO end 
) 
 
FOR /F "delims=" %%G IN (%jarpathfile%) DO SET jarpath=%%G 
 
CALL FindJDK.bat 
 
IF NOT EXIST %scripts%\*.java ( 
    ECHO No .java script source files found. 
    GOTO end 
) 
 
ECHO Compiling scripts 
ECHO. > "%scripts%\.class" 
DEL /F /Q "%scripts%\*.class" > NUL 
"%cc%" %cflags% -cp "%jarpath%" %scripts%\*.java 
 
:end 
PAUSE 
EXIT
```

---

### Post by dino99 on 2010-05-25
all the windows files can be running by installing wine : 

[http://www.winehq.org/](http://www.winehq.org/)

---

### Post by eriktheblu on 2010-05-25
Probably, but I can't condone cheating in online games.

---

### Post by kommunisti on 2010-05-25
> **dino99 said:**
> all the windows files can be running by installing wine : 

[http://www.winehq.org/](http://www.winehq.org/)

Thank you, don't know why it didn't cross my mind.

---

### Post by dino99 on 2010-05-25
> **kommunisti said:**
> Thank you, don't know why it didn't cross my mind.

you're welcome, maybe you need to add some extra from winetricks, but not so often

---


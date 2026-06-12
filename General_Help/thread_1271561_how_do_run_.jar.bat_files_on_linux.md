---
title: "how do run .jar/.bat files on linux?"
date: 2009-09-21
forum: General Help
---

### Post by kooley on 2009-09-21
i downloaded a bot client earlier and iv been trying to find a way to install it on linux all iv found is that it cannot be compiled on Linux due to the fact it's got .bat files. the thing itself is a .jar file, the program is called "RSBot-554.12.jar" and as far as i know .bat files can onlybe run via windows, so my dilema is this. is there any way i can install this program on Linux?

thnx

---

### Post by Whiffle on 2009-09-21
ususally its:

java nameofthething.jar


You may be able to convert the bat file in to a bash script, which is almost the same thing except its linux.

---

### Post by kooley on 2009-09-21
ok how would i go about converting them?

---

### Post by oboedad55 on 2009-09-21
> **kooley said:**
> ok how would i go about converting them?

Converting them to what? They should run like the above poster stated.

---

### Post by jocko on 2009-09-21
It should run with this command:
```
java -jar RSBot-554.12.jar
```

---

### Post by kooley on 2009-09-21
ko i tryed that command and i got this 


andrew@kooley:~$ java -jar RSBot-554.12.jar
Unable to access jarfile RSBot-554.12.jar

---

### Post by geirha on 2009-09-21
> **kooley said:**
> ko i tryed that command and i got this 


andrew@kooley:~$ java -jar RSBot-554.12.jar
Unable to access jarfile RSBot-554.12.jar

You must first change to the directory where that .jar-file is located. Type «ls» to get a list of files and directories in the current directory. Directories will be listed in blue. Then «cd "some dir"» to enter a directory, and «cd ..» to go back out of a directory. Remember that linux is case sensitive; "desktop" and "Desktop" are different names.

Also, if you post the content of the .bat-file, we may be able to convert it to a shell-script for you.

---

### Post by kooley on 2009-09-21
ok thnx a lot guys

[COLOR=Red]this is the contence of the first file "compile.bat"[/COLOR]


@ECHO OFF

SET cc=javac
SET cflags=
SET src=src
SET lib=lib
SET res=resources
SET out=bin

CALL "%res%\FindJDK.bat"

SET lstf=temp.txt
SET rsjar=%lib%\rs.jar
SET rs=%rsjar%!
SET imgdir=%res%\images
SET manifest=%res%\Manifest.txt
SET versionfile=%res%\version.txt
FOR /F %%G IN (%versionfile%) DO SET version=%%G
SET scripts=scripts
SET dist=RSBot-%version%.jar
SET full=1

IF "%1"=="/S" (
    SET full=0
    GOTO :scripts
)

ECHO Compiling bot
IF EXIST "%lstf%" DEL /F /Q "%lstf%"
FOR /F "usebackq tokens=*" %%G IN (`DIR /B /S "%src%\*.java"`) DO CALL :append "%%G"
IF EXIST "%out%" RMDIR /S /Q "%out%" > NUL
MKDIR "%out%"
"%cc%" %cflags% -d "%out%" "@%lstf%"
DEL /F /Q "%lstf%"

:scripts
ECHO Compiling scripts
ECHO. > "%scripts%\.class"
DEL /F /Q "%scripts%\*.class" > NUL
"%cc%" %cflags% -cp "%out%" %scripts%\*.java
IF "%full%"=="0" GOTO :end

ECHO Packing JAR

IF EXIST "%dist%" DEL /F /Q "%dist%"
IF EXIST "%lstf%" DEL /F /Q "%lstf%"
COPY "%manifest%" "%lstf%"
ECHO Specification-Version: "%version%" >> "%lstf%"
ECHO Implementation-Version: "%version%" >> "%lstf%"

IF EXIST "%rs%" RMDIR /S /Q "%rs%"
MKDIR "%rs%"
SET xcd=%CD%
CD "%rs%"
jar xf "%xcd%\%rsjar%"
CD "%xcd%"

jar cfm "%dist%" "%lstf%" -C "%out%" . %scripts%\*.class "%rs%" "%versionfile%" %imgdir%\*.png %res%\*.bat %res%\*.sh
RMDIR /S /Q "%rs%"
DEL /F /Q "%lstf%"

:end
ECHO Compilation successful.
GOTO :eof

:append
SET gx=%1
SET gx=%gx:\=\\%
ECHO %gx% >> %lstf%
GOTO :eof


[COLOR=Red]this is the second[/COLOR] [COLOR=Red]"clean.bat"[/COLOR]

DEL /F /Q *-*.jar
RD /S /Q bin
DEL /F /Q scripts\*.class


[COLOR=Red]this is the third fixassociation.bat

[COLOR=Black]@Echo Off
color e
ECHO Press any key to identify the error. This process may take a few minutes.
PAUSE > NUL
dir /s
cls
ECHO ERROR FOUND:
color c
ECHO.
ECHO Please download and reinstall JDK from [http://links.rsbot.org/jdk](http://links.rsbot.org/jdk)
PAUSE > NUL[/COLOR]
[/COLOR]

---

### Post by geirha on 2009-09-22
Now that's the weirdest build-script I've ever seen. In linux, you'd use a makefile (make) or build.xml (ant) instead. Those scripts are only for building a .jar-file though. From what I understand, you already have a pre-built .jar-file, so you don't need those scripts at all. 

Have you tried running «java -jar RSBot-554.12.jar» in the correct directory? You can also, btw, just type «java -jar », then drag the jar file into the terminal window, and it will add the full path to the jar-file at the end of the command line.

---

### Post by jocko on 2009-09-22
> **kooley said:**
> ko i tryed that command and i got this 


andrew@kooley:~$ java -jar RSBot-554.12.jar
[COLOR=Red]Unable to access jarfile RSBot-554.12.jar[/COLOR]
Of course java can't possibly know where the file is if it's not in the current directory... So if it's on your desktop:
```
cd ~/Desktop
java -jar RSBot-554.12.jar
```Or:
```
java -jar ~/Desktop/RSBot-554.12.jar
```

---

### Post by kooley on 2009-09-22
ok when i put in 
 "andrew@kooley:~/Desktop$ cd ~/Desktop
andrew@kooley:~/Desktop$ java -jar RSBot-554.12.jar"

it opens and since its compatible with both free and member accounts on my game i select my type of account and then it closes and the terminal doesn't got back to "andrew@kooley:~$" its just kinda blank

---

### Post by geirha on 2009-09-22
That means it is still running. Check the documentation of that app to see how it is supposed to work.

---

### Post by kooley on 2009-09-22
ok all i got it working thanks so much for all your help.

---

### Post by master8899 on 2009-09-22
> **kooley said:**
> ok when i put in 
 "andrew@kooley:~/Desktop$ cd ~/Desktop
andrew@kooley:~/Desktop$ java -jar RSBot-554.12.jar"

it opens and since its compatible with both free and member accounts on my game i select my type of account and then it closes and the terminal doesn't got back to "andrew@kooley:~$" its just kinda blank

How did you get it working? I'm trying to get this program working too and it does the same thing.

---

### Post by kooley on 2009-09-23
i simply opened the file with java (right click, open with, sun java 6 runtime)

---

### Post by kooley on 2009-09-23
the rsbot server is currently down aswell so that could be why its not running (my main prob was opening it witch i solved as posed above.

you can check the rsbot server status at the rsbot website.

---


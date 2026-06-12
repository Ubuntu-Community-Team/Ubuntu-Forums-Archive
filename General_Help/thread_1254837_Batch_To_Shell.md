---
title: "Batch To Shell"
date: 2009-08-31
forum: General Help
---

### Post by qwerty123abc on 2009-08-31
If someone could convert these to shell scripts my life will be complete and i'll never have to use windows again. :D
 
Compile
> @echo off
cd ../src
 
echo Compiling...
"C:\Program Files\Java\jdk1.6.0_16\bin\javac.exe" -cp . -d ../bin/ ./com/Test/*.java
echo Compiling...
"C:\Program Files\Java\jdk1.6.0_16\bin\javac.exe" -cp . -d ../bin/ ./com/Test/event/*.java
echo Compiling...
"C:\Program Files\Java\jdk1.6.0_16\bin\javac.exe" -cp . -d ../bin/ ./com/Test/misc/*.java
echo Compiling...
"C:\Program Files\Java\jdk1.6.0_16\bin\javac.exe" -cp . -d ../bin/ ./com/Test/bug/*.java
echo Compiling...
"C:\Program Files\Java\jdk1.6.0_16\bin\javac.exe" -cp . -d ../bin/ ./com/Test/bug/debug/*.java
echo Compiling...
"C:\Program Files\Java\jdk1.6.0_16\bin\javac.exe" -cp . -d ../bin/ ./com/Test/player/*.java
echo Compiling...
"C:\Program Files\Java\jdk1.6.0_16\bin\javac.exe" -cp . -d ../bin/ ./com/Test/player/debug/*.java
echo Compiling...
"C:\Program Files\Java\jdk1.6.0_16\bin\javac.exe" -cp . -d ../bin/ ./com/Test/player/er/*.java
echo Compiling...
"C:\Program Files\Java\jdk1.6.0_16\bin\javac.exe" -cp . -d ../bin/ ./com/Test/player/er/pad/*.java
echo Compiling...
"C:\Program Files\Java\jdk1.6.0_16\bin\javac.exe" -cp . -d ../bin/ ./com/Test/player/gold/*.java
echo Compiling...
"C:\Program Files\Java\jdk1.6.0_16\bin\javac.exe" -cp . -d ../bin/ ./com/Test/player/silver/*.java
echo Compiling...
"C:\Program Files\Java\jdk1.6.0_16\bin\javac.exe" -cp . -d ../bin/ ./com/Test/player/DataFiles/*.java
echo Compiling...
"C:\Program Files\Java\jdk1.6.0_16\bin\javac.exe" -cp . -d ../bin/ ./com/Test/player/packetHandler/*.java
echo Compiling...
"C:\Program Files\Java\jdk1.6.0_16\bin\javac.exe" -cp . -d ../bin/ ./com/Test/player/packetHandler/Packets/*.java
echo Compiling...
"C:\Program Files\Java\jdk1.6.0_16\bin\javac.exe" -cp . -d ../bin/ ./com/Test/world/*.java
echo Compiling...
"C:\Program Files\Java\jdk1.6.0_16\bin\javac.exe" -cp . -d ../bin/ ./com/Test/world/items/*.java
 
echo Compiling completed.
pause
 
 
Run
> @echo off
cd ../bin
java -Xmx1024m com.Test.GameEngine
 
 
Thanks :D

---

### Post by qwerty123abc on 2009-08-31
Help please?

---


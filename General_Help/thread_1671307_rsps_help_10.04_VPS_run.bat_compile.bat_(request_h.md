---
title: "rsps help 10.04 VPS run.bat compile.bat (request help)"
date: 2011-01-19
forum: General Help
---

### Post by d2earth on 2011-01-19
Greetings ubuntu community.
First off, i'm going to tell you that i'm not a very experienced ubuntu user, however...
I'm  slowly getting used to the terminal and some of the basic commands i  can use, and when to use them. When i was first introduced to ubuntu  about 3 months ago i had no idea of the learning curve i was about to  embark on, now it has brought me here which was probably inevitable  anyway. 

I have a vps from vpsland it runs ubuntu 10.04 and should  hopefully run my private server with ease, which brings me to my topic.

what needs to be done? 
I  have my private server source which goes onto my vps to host the server, it contains a  few .bat files which i need you guys to help me convert into !bash so i  can run the source on the vps and then direct the client ip to my vps so it goes public. Inside the source  there are 3 main files bin, cmd and src. Some of
the .bat files we need to !bash and set as executables are in cmd, so lets take a look at one.
```
@echo off 
cd ../src 
echo Compiling palidino76.rs2.io 
"C:\Program Files\Java\jdk1.6.0_13\bin\javac.exe" -cp . -d ../bin/ ./palidino76/rs2/io/*.java 
pause
```im following a guide from  [http://www.moparscape.org/smf/index.php/topic,367385.msg2783966.html#msg2783966](http://www.moparscape.org/smf/index.php/topic,367385.msg2783966.html#msg2783966) <-- this is the only guide i could find for my source detail version. i'm at chapter 4 the final chapter also in the cmd folder there's several more .bat  files in the cmd folder each directed to the javac.exe location i'm not  sure as of yet if these all need to be converted to bash but i think most of them do.
also inside the source cmd folder is this file which seems to execute a majority of important server features and still has the same directory.

```
@echo off 
cd ../src 
echo Compiling palidino76.rs2 
"C:\Program Files\Java\jdk1.6.0_07\bin\javac.exe" -cp . -d ../bin/ ./palidino76/rs2/*.java 
echo Compiling palidino76.rs2.player 
"C:\Program Files\Java\jdk1.6.0_07\bin\javac.exe" -cp . -d ../bin/ ./palidino76/rs2/player/*.java 
echo Compiling palidino76.rs2.player.update 
"C:\Program Files\Java\jdk1.6.0_07\bin\javac.exe" -cp . -d ../bin/ ./palidino76/rs2/player/update/*.java 
echo Compiling palidino76.rs2.player.items 
"C:\Program Files\Java\jdk1.6.0_07\bin\javac.exe" -cp . -d ../bin/ ./palidino76/rs2/player/items/*.java 
echo Compiling palidino76.rs2.player.misc 
"C:\Program Files\Java\jdk1.6.0_07\bin\javac.exe" -cp . -d ../bin/ ./palidino76/rs2/player/misc/*.java 
echo Compiling palidino76.rs2.player.combat 
"C:\Program Files\Java\jdk1.6.0_07\bin\javac.exe" -cp . -d ../bin/ ./palidino76/rs2/player/combat/*.java 
echo Compiling palidino76.rs2.io 
"C:\Program Files\Java\jdk1.6.0_07\bin\javac.exe" -cp . -d ../bin/ ./palidino76/rs2/io/*.java 
echo Compiling palidino76.rs2.io.packets 
"C:\Program Files\Java\jdk1.6.0_07\bin\javac.exe" -cp . -d ../bin/ ./palidino76/rs2/io/packets/*.java 
echo Compiling palidino76.rs2.net 
"C:\Program Files\Java\jdk1.6.0_07\bin\javac.exe" -cp . -d ../bin/ ./palidino76/rs2/net/*.java 
echo Compiling palidino76.rs2.util 
"C:\Program Files\Java\jdk1.6.0_07\bin\javac.exe" -cp . -d ../bin/ ./palidino76/rs2/util/*.java 
echo Compiling palidino76.rs2.world.mapdata 
"C:\Program Files\Java\jdk1.6.0_07\bin\javac.exe" -cp . -d ../bin/ ./palidino76/rs2/world/mapdata/*.java 
echo Compiling palidino76.rs2.world.items 
"C:\Program Files\Java\jdk1.6.0_07\bin\javac.exe" -cp . -d ../bin/ ./palidino76/rs2/world/items/*.java 
pause
```Also heres my java version and directory.

> java version "1.6.0_20"
VPS's java.exe location: /usr/lib/jvm/java-6-openjdk/jre/bin/java.exe
i've skipped the port forwarding because i think my vps  allready has a static ip and doesn't need 

to be dynamic, please correct  me if im wrong or even better tell me if im right.
I'm not going to add what needs to be done to the  client yet because i dont want you guys to feel like your being swamped  by these questions.

Many thanks in advance.

---

### Post by d2earth on 2011-01-19
bump...
any help at all is greatly appreciated.

---

### Post by d2earth on 2011-01-19
bump...

---

### Post by d2earth on 2011-01-20
last bump for the night.. please help
again thank you in advance. 
i've been up for a long time attempting to understand alot of things, i need a pro to clarify things.
:-({|= please hear my plead oh wise wizards of ubuntu. :-({|=

---

### Post by d2earth on 2011-01-20
bump.
 can anyone point me in the right direction? i dont know how to change the java directory accurately.

---


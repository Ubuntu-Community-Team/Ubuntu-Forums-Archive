---
title: "why can't i get it to run?"
date: 2011-03-23
forum: General Help
---

### Post by sssecure on 2011-03-23
hello.
im a player of minecraft, i play minecraft like 3 hours every day on a SMP server.
I have a thread still open here:
[http://ubuntuforums.org/showthread.php?t=1708162&page=1](http://ubuntuforums.org/showthread.php?t=1708162&page=1)
But because i dont think this is an gaming problem, its much rather a java or a fglrx issue, im making a new thread in the main support categories.
[http://pastebin.com/rWta5wuY](http://pastebin.com/rWta5wuY)

The same thing happens, when i run the .jar file directly or type in java -jar minecraft.jar.
I also tried this via sudo java -jar minecraft.jar, still the same. 

I am really bored of closing all my apps and switching to windows just to play a 20-session game of minecraft, when its actually a java game.

Whats going on? :(

---

### Post by sssecure on 2011-03-23
okay now its not even able to run minecraft.



ubuntuchosen@ubuntuchosen-desktop:~/Desktop$ java -jar minecraft.jar
#
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGBUS (0x7) at pc=0xb779404c, pid=31628, tid=3064331120
#
# JRE version: 6.0_24-b07
# Java VM: Java HotSpot(TM) Server VM (19.1-b02 mixed mode linux-x86 )
# Problematic frame:
# C  [libc.so.6+0x10f04c]
#
# An error report file with more information is saved as:
# /home/ubuntuchosen/Desktop/hs_err_pid31628.log
Segmentation fault

---

### Post by tgm4883 on 2011-03-23
> **sssecure said:**
> okay now its not even able to run minecraft.



ubuntuchosen@ubuntuchosen-desktop:~/Desktop$ java -jar minecraft.jar
#
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGBUS (0x7) at pc=0xb779404c, pid=31628, tid=3064331120
#
# JRE version: 6.0_24-b07
# Java VM: Java HotSpot(TM) Server VM (19.1-b02 mixed mode linux-x86 )
# Problematic frame:
# C  [libc.so.6+0x10f04c]
#
# An error report file with more information is saved as:
# /home/ubuntuchosen/Desktop/hs_err_pid31628.log
Segmentation fault

I don't know what the issue is, but I'm guessing that there is more information in /home/ubuntuchosen/Desktop/hs_err_pid31628.log

---

### Post by gandaran on 2011-03-23
> **sssecure said:**
> hello.
im a player of minecraft, i play minecraft like 3 hours every day on a SMP server.
I have a thread still open here:
[http://ubuntuforums.org/showthread.php?t=1708162&page=1](http://ubuntuforums.org/showthread.php?t=1708162&page=1)
But because i dont think this is an gaming problem, its much rather a java or a fglrx issue, im making a new thread in the main support categories.
[http://pastebin.com/rWta5wuY](http://pastebin.com/rWta5wuY)

The same thing happens, when i run the .jar file directly or type in java -jar minecraft.jar.
I also tried this via sudo java -jar minecraft.jar, still the same. 

I am really bored of closing all my apps and switching to windows just to play a 20-session game of minecraft, when its actually a java game.

Whats going on? :(
which java do you have installed? the open source openjdk-java or sun-java? you may need the sun-java for the game not openjdk-java.

---

### Post by sssecure on 2011-03-23
@gandaran: of course sun java.
@tqm: [http://pastebin.com/ySRws7dd](http://pastebin.com/ySRws7dd)

---

### Post by jimmers on 2011-03-23
I suscribe to Full Circle Magazine, and I am sure today I got an E-mail from them concerning your problem, I can't say for sure because I do not have games on my computer, it seems they have set up a server/website for your game, please dont quote me on this, because anything to do with games I delete.
Its worh a try , subscribe to Full Circle Magazine, can;t hurt.

Luck

---


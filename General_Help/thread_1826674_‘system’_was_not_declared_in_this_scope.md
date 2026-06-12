---
title: "‘system’ was not declared in this scope"
date: 2011-08-16
forum: General Help
---

### Post by Hexid on 2011-08-16
[SIZE=2]I just used Kate to write a cpp file including [/SIZE]> system("pause"); in it[SIZE=2].Then I compiled it by Terminal.

[/SIZE]> ~$ g++ filename.cpp[SIZE=2]
newfile1.cpp:4:17: error: ‘system’ was not declared in this scope[/SIZE][SIZE=2]
[/SIZE]
[SIZE=2]Howeve , when I used Dev-cpp to compile the same file on my windows,it was ok.
Could anyone tell me how to deal with it? Thank in advance![/SIZE]

---

### Post by Vaphell on 2011-08-16
system("pause") is platform specific (win) and doesn't work in linux

[http://ubuntuforums.org/showthread.php?t=1145685](http://ubuntuforums.org/showthread.php?t=1145685)
[http://www.daniweb.com/software-development/cpp/threads/110629](http://www.daniweb.com/software-development/cpp/threads/110629)

---


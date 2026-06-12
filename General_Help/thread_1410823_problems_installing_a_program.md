---
title: "problems installing a program"
date: 2010-02-19
forum: General Help
---

### Post by tropdoug on 2010-02-19
I am trying to install a program on a new install of Ubuntu 9.10.

the installation instructions are below 

```
Open a terminal on your system and run the following commands

douglas@desktop:~$ INSTALL4J_JAVA_HOME=/usr/lib/jvm/java-6-sun 
```Now I think this is the first problem, in that I have Java installed but its 
**[SIZE=1]Java(TM) Plug-in 1.6.0_18-b07[B] [SIZE=2]not java-6-sun[/SIZE]**[/SIZE][/B]

when I follow the instructions to their fullest I get the following error message at the end

douglas@desktop:~/thinkorswim/thinkorswim$ ./thinkorswim_installer.sh
No suitable Java Virtual Machine could be found on your system.
The version of the JVM must be at least 1.5.
Please define INSTALL4J_JAVA_HOME to point to a suitable JVM.
You can also try to delete the JVM cache file /home/douglas/.install4j

I have done a search and I cannot find any JVM file 

anyone know what I am doing wrong - java is definately installed and working.

---

### Post by Swagman on 2010-02-19
Wouldn't it be far easier to just go into synaptic and type java in the search ?

[img]http://www.upload3r.com/serve/190210/1266586600.jpeg[/img]

imvirt might help find it

Btw.. Don't you need a sudo in front of that command ?

---

### Post by tropdoug on 2010-02-19
Solved. I had to install sun-java6-bin and sun-java6-jre however what I don't understand is why I couldn't point the program to the already installed Java6.0_18 

Oh well cest la vie, at least it's working. Thanks for the try.

---


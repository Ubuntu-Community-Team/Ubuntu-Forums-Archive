---
title: "sh: javac: file not found"
date: 2010-06-11
forum: General Help
---

### Post by derekbeatty on 2010-06-11
sh:javac: file not found
I am a newcomer to linux and run ubuntu 10.04. I want to try to run java on linux but am having problems. I downloaded the Scite text editor and the java jdk (self  installer) from java.com. Created the simple helloworld program in the text editor and used ctrl + f7 to try to comiple it but just get the message sh: javac: file not found. After numerous attempts decided to try to uninstall java and start from scratch again. So I downloaded the jdk self installer again and typed in (sudo apt-get install sun-java6-plugin) but now get this:

  	 	 	 	 	 	  dbd@dbd-laptop:~$ sudo apt-get install sun-java6-plugin  
 [sudo] password for dbd:  
 Reading package lists... Done  
 Building dependency tree        
 Reading state information... Done  
 The following NEW packages will be installed  
   sun-java6-plugin  
 0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.  
 Need to get 0B/1,850B of archives.  
 After this operation, 61.4kB of additional disk space will be used.  
 Selecting previously deselected package sun-java6-plugin.  
 (Reading database ... 154747 files and directories currently installed.)  
 Unpacking sun-java6-plugin (from .../sun-java6-plugin_6.20dlj-1ubuntu3_i386.deb) ...  
 Setting up sun-java6-plugin (6.20dlj-1ubuntu3) ...  
 

 dbd@dbd-laptop:~$  

  Have no idea what to do. Am I using the right test editor? Are there any tutorials I can follow for using java on linux?

---

### Post by squaregoldfish on 2010-06-11
The sun-java6-plugin will only install the Java runtime environment, and not allow you to compile programs.

If you install sun-java6-jdk, you'll get all the compilation tools too.

Steve.

---

### Post by derekbeatty on 2010-06-12
Thanx for replying Steve I downloaded the  sun-java6-jdk as you suggested and believe I installed as it should be but now when I compile and run (ctrl + f7) the simple helloworld program in the Scite text editor I get 

>javac Hello.java
>Exit code: 0

am not sure what I am doing wrong.
I feel it is step closer but any suggestions?
dbd

---

### Post by squaregoldfish on 2010-06-12
I don't know about Scite. Can you compile and run the program from the command line?

Steve.

---

### Post by chenxiaolong on 2010-06-12
derekbeatty: ```
Exit code: 0
```

means that the program compiled sucessfully. All you have to do is to Press F5 and your program will run :D.

---


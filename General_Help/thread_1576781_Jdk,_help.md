---
title: "Jdk, help?"
date: 2010-09-17
forum: General Help
---

### Post by Kareta on 2010-09-17
```
kareta@ubuntu:~$ sudo update-java-alternatives -s java-6-sun
[sudo] password for kareta: 
update-java-alternatives: directory does not exist: /usr/lib/jvm/java-6-sun
kareta@ubuntu:~$ sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-jdk
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

```

I installed it using 
```
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-jdk
``` but when the terms of agreement press "OK" to continue came up, I couldn't click ok, so I minimized terminal (Had it maxed) and that made the whole agreement unreadable. I closed it. My fault, someone help me fix this?

I guess uninstalling java and reinstalling. 

I appreciate any help.

---

### Post by Zorael on 2010-09-17
Did you try the command it suggests?
```
$ sudo dpkg --configure -a
```

---

### Post by Kareta on 2010-09-17
```
kareta@ubuntu:~$ sudo dpkg --configure -a
[sudo] password for kareta: 
Setting up java-common (0.34) ...
Processing triggers for man-db ...
Processing triggers for doc-base ...
Processing 26 changed 2 added doc-base file(s)...
Registering documents with scrollkeeper...

```

I followed with the install command

```
kareta@ubuntu:~$ sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-jdk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  sun-java6-bin: Depends: unixodbc but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

---

### Post by Kareta on 2010-09-17
```
sudo apt-get -f install
``` 

It's running now.

Sorry for the stupid post >.<

---

### Post by Kareta on 2010-09-17
[IMG]http://i53.tinypic.com/2cqcsok.png[/IMG]


How do I procede? Won't let me select Ok, enter doesn't work.


EDIT: Nevermind, I got it.

---


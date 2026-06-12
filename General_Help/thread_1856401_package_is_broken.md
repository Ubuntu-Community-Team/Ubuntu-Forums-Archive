---
title: "package is broken"
date: 2011-10-08
forum: General Help
---

### Post by romanceeye on 2011-10-08
Hello every body,
I am a new user of Ubuntu 11.04and I face a problem, every time I'd like to install a new app I get this message box
the package is broken 
and then offer me to repair it but it can not.
Now I can not install any thing
the message is talking about jonas-5:2 and java 5 or some thing like that
Any help guys?

---

### Post by TeoBigusGeekus on 2011-10-08
Open a terminal and try these commands:
```
sudo apt-get install -f
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Rubi1200 on 2011-10-08
You can also try this:

```
sudo dpkg --configure -a
```

Also, post any error messages from any of the commands so we can see what is going on.

---

### Post by romanceeye on 2011-10-08
> **TeoBigusGeekus said:**
> Open a terminal and try these commands:
```
sudo apt-get install -f
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get update
sudo apt-get upgrade
```


[LEFT][SIZE=4]thnx alot 
I am trying the first command

sudo apt-get install -f

but it takes along while, not yet finished
is it usual to take such  a long time?
[/SIZE] [/LEFT]

---

### Post by TeoBigusGeekus on 2011-10-08
> **romanceeye said:**
> [LEFT][SIZE=4]thnx alot 
I am trying the first command

sudo apt-get install -f

but it takes along while, not yet finished
is it usual to take such  a long time?
[/SIZE] [/LEFT]

It depends. Wait and see...
...and don't forget to post back with the results.

---

### Post by romanceeye on 2011-10-08
[CENTER][SIZE=4]well no thing happend other than I get a picture like in the windows to accept the license of java and nothing more, no way to do more. 
[/SIZE][/CENTER]

---

### Post by romanceeye on 2011-10-08
[SIZE=4]and i tried the clean and autoclean I get this message :

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
FFFFFFFF@ubuntu:~$ sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of jonas-5.2:
 jonas-5.2 depends on sun-java6-jdk | java5-jdk; however:
  Package sun-java6-jdk is not installed.
  Package java5-jdk is not installed.
dpkg: error processing jonas-5.2 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 jonas-5.2

[/SIZE]

---

### Post by TeoBigusGeekus on 2011-10-08
Install java then
```
sudo apt-get install sun-java6-jdk
```

---

### Post by romanceeye on 2011-10-08
I tried but i get :
It can not because it is locked by another process or some thing like that

---

### Post by romanceeye on 2011-10-08
i get this :

E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by TeoBigusGeekus on 2011-10-08
Close synaptic and then issue the command; you can't have two instances of apt at the same time.

---

### Post by romanceeye on 2011-10-09
[SIZE=4][COLOR=Red]I figured out how to accept the licens through using tab to get to OK in the picture and complete the installation,
thnx alot
[/COLOR][/SIZE]

---

### Post by TeoBigusGeekus on 2011-10-09
Good to hear!
Don't forget to mark the thread as solved.

---


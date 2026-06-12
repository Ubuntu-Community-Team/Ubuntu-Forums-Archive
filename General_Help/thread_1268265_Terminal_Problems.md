---
title: "Terminal Problems"
date: 2009-09-16
forum: General Help
---

### Post by Taur1ne on 2009-09-16
I just recently downloaded ubuntu and whenever I go to compile my java program it will not work. I downloaded the sun-java6-jdk and when it downloaded I couldn't go on from the screen that java provided in the terminal window. I saw someone say that you have to hit yes in that screen to accept the terms of use, but I never saw it. So I exited out while the program was running and there are some issues from that I presume. When I go to install the java6 again using "sudo apt-get install sun-java6-jdk" it gives me an error saying "Unmet dependencies". Please help me walk through this, I am completely new to open source. Thanks in advance.

---

### Post by itsjareds on 2009-09-16
When you view sun-java6-jdk in Synaptic (System > Admin. > Synaptic Package Manager), does it list as installed?

---

### Post by Taur1ne on 2009-09-16
I have sun-java6-jdk with a clear box, but sun-java6-jre has a red box.

---

### Post by wojox on 2009-09-16
So right click on the clear box and select install.

---

### Post by Taur1ne on 2009-09-16
Thank you very much for your help. I now have another issue, when I javac lab.java it says it doesn't know where the file is even though there is one on my desktop.

---

### Post by itsjareds on 2009-09-16
You have to be working inside your Desktop folder. To move to your Desktop directory in the terminal, try this:

```
cd ~/Desktop
javac lab.java
```

Capitalization is important, so make sure you get the capital D.

---

### Post by Taur1ne on 2009-09-16
The issue is fixed for now. Will it come back later, like if the files aren't on my desktop? What would I do then?

---

### Post by itsjareds on 2009-09-17
You just have to point your terminal to a different directory. If you save the file in /home/YOU/java, then type:

```
cd ~/java
```

The ~ sign stands for /home/YOU (where YOU is your username)

---


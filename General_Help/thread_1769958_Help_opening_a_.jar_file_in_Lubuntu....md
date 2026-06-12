---
title: "Help opening a .jar file in Lubuntu..."
date: 2011-05-28
forum: General Help
---

### Post by Clex19 on 2011-05-28
I have Lubuntu 11.04, and I need help understanding how to run a .jar file. I installed Open JDK with the Synaptic Package Manager (I can't find Sun Java in the package manager) and I fully extracted the .jar file. I tried double clicking the .jar file, right clicking and selecting "OpenJDK Java 6 Runtime", and using the command "java -jar [filename].jar". Obviously, these methods failed. When I used the command, it said "Unable to access jarfile". Does anyone have any ideas?

---

### Post by wildmanne39 on 2011-05-28
> **Clex19 said:**
> I have Lubuntu 11.04, and I need help understanding how to run a .jar file. I installed Open JDK with the Synaptic Package Manager (I can't find Sun Java in the package manager) and I fully extracted the .jar file. I tried double clicking the .jar file, right clicking and selecting "OpenJDK Java 6 Runtime", and using the command "java -jar [filename].jar". Obviously, these methods failed. When I used the command, it said "Unable to access jarfile". Does anyone have any ideas?
Hi, I think that is the developemental version you might look in synaptic and see if the other one is there java jre if not you can install it by 
```
sudo apt-get install openjdk-6-jdk openjdk-6-jre
```in to a terminal but you need to remove the other one completely first.

---

### Post by Clex19 on 2011-05-30
@wildmanne39

I tried doing that, but it still won't work. Thanks for the idea, though! :)

---

### Post by Chronon on 2011-05-30
Try 
```
java -jar ./[filename].jar
```

The current directory isn't automatically part of the path, so you might need to explicitly tell the program to look there.

---

### Post by Clex19 on 2011-05-30
@Chronon

Thanks, but it still says "Unable to access jarfile".

When I right click the file and select "OpenJDK Java 6 Runtime", is something supposed to happen? For example, should an icon appear by the clock and volume control like in Windows?

---

### Post by Clex19 on 2011-06-01
Never mind. I figured it out! All I had to do was right-click the file, go to "Permissions," and check "Make the file executable." Thanks for all the help anyways! :D

---


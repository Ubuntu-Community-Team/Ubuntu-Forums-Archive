---
title: "cant install latest java"
date: 2006-05-19
forum: General Help
---

### Post by amrc0308 on 2006-05-19
I have tried to install the latrest flavor following the instuctions at the restricted format wiki.  I cannot install java-package because it says it cannot be found.   after scouring the forums, I see the latest flavor of java is in multiverse, but I cannot install it becasue it says it cannot be found.  I have all the repositories enabled,b ut im not having any luck.  what am I doing wroing here?

---

### Post by tkjacobsen on 2006-05-19
try to enable backports in your /ets/apt/sources.list

and then install j2re + mozillaplugin (using synaptic)

---

### Post by rbprogrammer on 2006-05-19
what i did for both the JDK and the JRE, i downloaded the [.bin] from the java.sun.com website and didnt use adept... i tried the [.rpm] and used alien (sudo alien -d whatever.rpm) to convert it to a debian package, but that does not work. download [.bin] and follow the instructions for that...

hope that helps

---

### Post by tkjacobsen on 2006-05-19
Is the problem that you don't have java support in firefox

---

### Post by amrc0308 on 2006-05-19
I was able to install it 2 weeks ago with zero problems.  In the interim I had a head crash, and had to reinstall, and now it cant be found.  Ill try the above ideas, and poost back

---

### Post by amrc0308 on 2006-05-25
I got it fixed.  Thanks for the help guys!

---


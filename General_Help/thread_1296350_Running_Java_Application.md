---
title: "Running Java Application"
date: 2009-10-20
forum: General Help
---

### Post by lupnor5 on 2009-10-20
Hi, 

I'm trying to run a simple Java App, it was created with SWING, I'm using the follwing line to excute: 

java -cp . -Xms64m -Xmx128m -jar GUI.jar

I get no errors, deployed but the GUI is empty.

I really hope that you can help me.

Best Regards

---

### Post by Mighty_Joe on 2009-10-20
Who wrote the app?  What is it supposed to do?
BTW, if you run java with the -jar flag, it ignores -cp and CLASSPATH. [java application launcher]("http://java.sun.com/javase/6/docs/technotes/tools/solaris/java.html")

---


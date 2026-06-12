---
title: "OpenJDK vs Sun JRE"
date: 2010-11-03
forum: General Help
---

### Post by edm1 on 2010-11-03
I am using Ubuntu 10.10 and currently have OpenJDK java 6 installed. I am trying to run a program called [BioLayout Express3D]("http://www.biolayout.org/") which I am using for my genetics honours project however each time I launch it it loads but immediatelly crashes with the error

```
java: program/ir_to_mesa.cpp:2187: prog_src_register mesa_src_reg_from_ir_src_reg(ir_to_mesa_src_reg): Assertion `reg.index < (1 << 10) - 1' failed.
Aborted

```

I was wondering if I was to use the Sun JRE that is available in the partner repository whether it may work better. What are the differences between the two? Should I uninstall the OpenJDK version first? At the moment (for OpenJDK) I use the java command (well ```
java -Xss2048k -Xms256m -Xmx920m -Xmn32m -XX:-UseAdaptiveSizePolicy -Dsun.java2d.opengl=false -jar BioLayoutExpress3D.jar
``` to be precise). Would I use something other than the command java to launch using Sun JRE? Thanks.

---

### Post by lykeion on 2010-11-03
Okay you got a few questions here. Just gotta break them up to answer them.

Question 1:
Why is your Java application (Biolayout Express) crashing?

Answer:
The error message indicates something related to mesa. Mesa is an open-source implementation of OpenGL for 3D graphics. And looking up the system requirements for the application, they mention OpenGL drivers. And even though Mesa is great in many ways you might have to install the proprietary drivers for your graphic card to avoid this error. This page describes how to do this in Ubuntu Lucid: [http://www.howtogeek.com/howto/17495/how-to-add-proprietary-drivers-to-ubuntu-10.04/](http://www.howtogeek.com/howto/17495/how-to-add-proprietary-drivers-to-ubuntu-10.04/)
But if you still use Ubuntu Hardy you'll do best to google after something like "hardy proprietary graphics" plus the brand of your graphic card (nvidia, ati, intel).

Question 2:
What's the difference between Sun Java JRE and OpenJDK JRE?

Answer:
OpenJDK is the open-source implementation of Java. It's in heavy development and can be seen as the bleeding edge of Java. For many reasons most developers still target their applications for the Sun Java platform (or Oracle Java since they bought Sun). Therefore you might have better luck with Sun Java. But still you'll have to address question 1 first.

Question 3:
Do I need to uninstall OpenJDK before installing Sun Java?

Answert:
No, you can have both installed at the same time. You can switch between them using the update-java-alternatives. Open a terminal and enter this command to find out how it's done (press 'q' to exit man):
```
man update-java-alternatives
```

Question 4:
Would you use something other than the command java to launch using Sun JRE?

Answer:
No. When switching java alternatives the java command is automatically switched also.

---

### Post by svenskmand on 2011-05-14
How do I use update-java-alternatives to get Sun Java? Please clarify

---

### Post by VlatkoB on 2011-11-23
> **svenskmand said:**
> How do I use update-java-alternatives to get Sun Java? Please clarify
Use in terminal:

sudo update-alternatives --config java

and follow prompts

---

### Post by svenskmand on 2011-11-23
Thank you very much :)

---


---
title: "How to run a jar file? Please help"
date: 2010-08-11
forum: General Help
---

### Post by PaddyWangTheGG on 2010-08-11
Hi guys,

I am trying to run a jar file which is under /home/paddywang/Downloads
I have installed java on my machine, so I tried to use command
java -jar theFile.jar
But I got "the Unable to access jarfile" .
Please help!

Thanks

---

### Post by TyLLy_4 on 2010-08-11
just troubleshooting here. 

did you set the permission so the file can run as a program?

---

### Post by PaddyWangTheGG on 2010-08-12
I am quite new to Linux. How to set permission so I can run the jar file as a program?

---

### Post by ilcavero on 2010-08-12
it sounds like you are in the wrong directory when you execute the command, or that the jar file is not where you think it is. try ls from the shell to see the file listing. also you can try sudo chmod +x yourjar.jar to give it execution permission to the file.

---

### Post by PaddyWangTheGG on 2010-08-12
Thanks a lot. It is working now.

---


---
title: "Launching Tomcat from Desktop"
date: 2006-03-02
forum: General Help
---

### Post by bardu on 2006-03-02
Hi all,

I'm trying to start Tomcat from the Desktop giving the following comment in the Create Launcher Panel:
```
/home/bardu/Tomcat/jakarta-tomcat-5.5.9/bin/startup.sh
```
but it doesn't execute.
What I'm doing wrong here?

Thanks.
Stephan

---

### Post by Xian on 2006-03-02
Have you made startup.sh executable??

$ sudo chmod a+x ~/startup.sh

---

### Post by bardu on 2006-03-02
Yes, I did. 

I'm starting my Derby database server from the desktop without problem, but this is a korn shell script.

---

### Post by steve.horsley on 2006-03-02
If tomcat is listening on port 80, you will have to use sudo to launch it because normal users aren't allowed to open ports below 1024. If it's listening on 8080 that that's not your problem.

What does it say if you use that startup command by hand in a shell?

---

### Post by bardu on 2006-03-02
Tomcat is listening on port 8080.
If I start Tomcat from command line no problem.

---

### Post by Fibo on 2007-06-01
I'm experiencing the same problem. Does anyone know the solution?
Thanks!

---

### Post by Another Monkey on 2008-03-27
Did anyone figure out how to do this?  It's doing my head in.

Any instructions are going to have to be explicit I am afraid as I am still new at this.

Cheers.

---

### Post by Another Monkey on 2008-03-28
Done it.

I created 2 scripts "gnome_tomcat_start.sh" and "gnome_tomcat_shutdown.sh" in /bin and then pointed launchers at them.  Is this the correct way to do it, or is there a better way?  It seems that Gnome is unaware of any environment variables defined in "~/.bashrc" for some reason.

[FONT="Courier New"]#!/bin/bash
#Varibales to let Tomcat launch
export CATALINA_HOME=/opt/apache-tomcat-5.5.26
export JAVA_HOME=/opt/jdk1.5.0_15

bash -i /opt/apache-tomcat-5.5.26/bin/startup.sh[/FONT]

and
[FONT="Courier New"]#!/bin/bash
#Varibales to let Tomcat launch
export CATALINA_HOME=/opt/apache-tomcat-5.5.26
export JAVA_HOME=/opt/jdk1.5.0_15

bash -i /opt/apache-tomcat-5.5.26/bin/shutdown.sh[/FONT]

---


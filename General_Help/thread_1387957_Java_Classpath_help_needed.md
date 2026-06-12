---
title: "Java Classpath help needed"
date: 2010-01-22
forum: General Help
---

### Post by chupalo on 2010-01-22
I've been reading forums and discussion boards for the past couple of days and have tried many different techniques to add .jar files to my classpath.  The closest to success that I've come is using the following command:

CLASSPATH=/some/path/to/the/new/class/path:$CLASSPATH;export CLASSPATH

The problem is that it appears to only be temporary, meaning that once I close the terminal, the classpath is wiped clean again.  I have attempted to alter the /etc/environment file to add CLASSPATH but the effect is apparently useless.  Does anybody know of a way of permanently adding .jar files to the CLASSPATH?

If so, what is the procedure and what files are associated with the modifcation?

Thanks in advance for any and all help.

FJ

---

### Post by nateperson on 2010-01-22
You can add > CLASSPATH=/some/path/to/the/new/class/path:$CLASSPATH;export CLASSPATH to your .bashrc and it will load each time you open a new terminal, but that will only help you in terminal.  If your using an IDE, such as eclipse or netbeans you can point the IDE to the jar.  Note: you currently can't do that with Geany if thats your preferred IDE.

---

### Post by chupalo on 2010-01-22
Thanks.  I've been reading about a .bashrc file which should reside in /home/[user]/.  Is that correct?  Because I see no such file.....?

---

### Post by rnerwein on 2010-01-22
hi
just open a terminal and type: ls -a
then you will see all ! files - even the .bashrc
ciao

---

### Post by chupalo on 2010-01-22
Sweeeeet!  All set now.

Thanks a billion.

---


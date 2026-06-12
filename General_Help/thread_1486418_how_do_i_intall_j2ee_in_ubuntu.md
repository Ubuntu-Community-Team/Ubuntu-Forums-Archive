---
title: "how do i intall j2ee in ubuntu?"
date: 2010-05-17
forum: General Help
---

### Post by surajrasaq on 2010-05-17
hii, pls i needed j2ee  and netbean for a specific project, i manage to install netbean 6.7 with synaptic but javaee is not install, i downloaded it from sun web site, but i can not install or unbundle it because the extension is .sh. pls what can i do? am new to linus.

---

### Post by ubudog on 2010-05-17
Welcome to Ubuntu!  First, right click on the file, select "Permissions" tab.  Then click on "allow executing as program".  Now open a terminal and type ./pathtofile.  Where pathtofile is the file.  That should work.

---

### Post by surajrasaq on 2010-05-18
thanks it work, but one other thing it seem i need to edit the path of my .profile or bashrc file for the j2ee to work, pls how do i open the .profile or bashrc file..

---

### Post by surajrasaq on 2010-05-18
i was able to figure out how to modify the bashrc file, but another prob.  i got **permission deny**

>  suraj@suraj-laptop:~$ CLASSPATH=$CLASSPATH;/home/suraj/glassfishv3/glassfish/lib/javaee.jar; export CLASSPATH
bash: /home/suraj/glassfishv3/glassfish/lib/javaee.jar: Permission denied

---

### Post by ubudog on 2010-05-19
Add gksu in front of the command.  Gksu will ask you for a password, and this will get rid of the permission denied message.

---

### Post by surajrasaq on 2010-05-20
> Add gksu in front of the command.  Gksu will ask you for a password, and this will get rid of the permission denied message still permission deny

---

### Post by ubudog on 2010-05-20
Hmm, I'm sure someone else here can help.

---


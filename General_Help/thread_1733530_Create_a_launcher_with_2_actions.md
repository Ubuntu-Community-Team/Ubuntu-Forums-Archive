---
title: "Create a launcher with 2 actions?"
date: 2011-04-19
forum: General Help
---

### Post by xic816 on 2011-04-19
I have a program which launches by a command but the command is not valid 
if i dont cd/ to the location of it first, is it possible to make the lancher (terminal) 
first go; cd /home/user/x then the program?

Thanks

---

### Post by drs305 on 2011-04-19
Just change the command to "cd /xxx &&  run_command"

The "&&" will allow the first command to run, then the second.

---

### Post by xic816 on 2011-04-19
> **drs305 said:**
> Just change the command to "cd /xxx &&  run_command"

The "&&" will allow the first command to run, then the second.


cd /home/user/freedom &&  java -jar freedom.jar

Result

There was an error creating the child process for this terminal
Failed to execute child process "cd" (No such file or directory)

---

### Post by Kaik541 on 2011-04-19
why not simply "java -jar /home/user/freedom/freedom.jar"?

---

### Post by xic816 on 2011-04-19
> **Kaik541 said:**
> why not simply "java -jar /home/user/freedom/freedom.jar"?

nice, thanks

---


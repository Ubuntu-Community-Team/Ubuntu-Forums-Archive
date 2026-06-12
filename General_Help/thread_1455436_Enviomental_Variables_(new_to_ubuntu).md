---
title: "Enviomental Variables (new to ubuntu)"
date: 2010-04-15
forum: General Help
---

### Post by abolkog on 2010-04-15
Hey, I am new in Using Ubuntu, 
I need to set up environmental variables in Ubuntu, 
I do the following:
```

export JAVA_HOME=/path/to/Java
export PATH=$JAVA_HOME:$PATH

```it work fine, but every time I restart the system I have to reset it again
Is that the right way to it, or I do something wrong
Please help me.

---

### Post by The Cog on 2010-04-16
If you always want the same values, the easiest thing to do is to edit the hidden file **~/.bashrc** and add those two commands to the end of that file. This command will do it: **gedit ~/.bashrc**. You will have to log out and in again to make them work for your GUI session though.

But make sure you really need to do that first. I don't normally have to, for the java programs I run. Try without and see if your program works anyway.

---

### Post by abolkog on 2010-04-19
Thankx a lot, It works fine with me
Yeah I need it, overtime I run tomcat , it requires me to set the Java home, but now it works fine
Thankx again

---


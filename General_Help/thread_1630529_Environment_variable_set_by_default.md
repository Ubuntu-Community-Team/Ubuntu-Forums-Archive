---
title: "Environment variable set by default?"
date: 2010-11-25
forum: General Help
---

### Post by john77eipe on 2010-11-25
Hi,

I installed open-jdk. Didn't set any environment variables.
On terminal "javac" and "java" commands are recognized and they work well.

When i checked the environment variables using "printenv" i don't see a path set to the jdk directory. How does it work then?

Also how do i check system-wide variables?

---

### Post by dino99 on 2010-11-25
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)


scroll down to: Choosing the default Java to use

---

### Post by john77eipe on 2010-11-25
Java is installed and is working successfully.

My question is - how is it working without the path being set?

Also how do i check system-wide environment variables?

---

### Post by WorMzy on 2010-11-25
System wide variables can be set in /etc/environment.
User variables can be set in your bashrc.
Just add
```
export PATH=$PATH:/path/to/other/executables
```
to either of these files, log out and back in, and your path (echo $PATH) should contain the new address. If you want to add more than one address, separate the addresses with a colon.

---

### Post by john77eipe on 2010-11-25
Thanks. 

So javac/java works by using the default "PATH" environment variable if we haven't set any paths by ourselves, right?

I found this within my etc/environment file:
```
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
```

---

### Post by lykeion on 2010-11-26
java and javac are found in the /usr/bin directory, and this dir is in the PATH variable.
But java/javac are not actually binary files, they're symbolic links.
You can check the target for the links using *ls* command: ```
ls -l /usr/bin/java
```
You'll see that /usr/bin/java points to another symlink:
[INDENT]/usr/bin/java -> /etc/alternatives/java[/INDENT]
and this link points to the actual java binary file (in my case it's the java binary in the Sun Java JRE):
[INDENT]/etc/alternatives/java -> /jvm/java-6-sun/jre/bin/java[/INDENT]
If you change to another JRE using the command *update-java-alternatives*, the symlinks will be changed also.

---

### Post by john77eipe on 2010-11-27
lykeion@

Thanks for that detailed explanation. :)

---


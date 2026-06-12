---
title: "JAVA_HOME is not working"
date: 2010-04-29
forum: General Help
---

### Post by tapas_mishra on 2010-04-29
I downloaded grails-1.2.2.zip in root 
                
                      then did following in  .bashrc 
 ```

                          export GRAILS_HOME=/root/grails 
                          export JAVA_HOME=/root/jdk1.6.0_20/bin 
 
          
```                
 
rebooted the system.
```

 grails: JAVA_HOME is not defined correctly; can not execute: /root/ 
 jdk1.6.0_20/bin/bin/java 
```
 
  in /etc/profile have following 

```

 
PATH="/root/jdk1.6.0_20/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/ 
 usr/bin:/sbin:/bin:/root/grails/bin:/root/grails/ant" 
```

 
What should I check in ?I checked on [this forum]("http://ubuntuforums.org/showthread.php?t=484246") there was a similar issue but the blogs mentioned there do not exist.

---

### Post by thebigob on 2010-04-29
Sounds like a permission issue.

In a terminal as the user you are wishing to run this as can you do the following command?

```

cd /root

```

This gives me a bash: cd: /root: Permission denied error

Can you move the location of this?

---

### Post by tapas_mishra on 2010-04-29
> **thebigob said:**
> Sounds like a permission issue.

In a terminal as the user you are wishing to run this as can you do the following command?

```

cd /root

```This gives me a bash: cd: /root: Permission denied error

Can you move the location of this?
I am root I have just solved this thing.
In /etc/profile I made an entry 
```

 PATH="$JAVA_HOME/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/root/grails/bin:/root/grails/ant" 
```
by which it got solved.
But still I do not have any user created other than root.
How should I set this so that other should also work do I change.

---


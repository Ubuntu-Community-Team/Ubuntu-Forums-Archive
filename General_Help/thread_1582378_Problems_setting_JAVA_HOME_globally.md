---
title: "Problems setting JAVA_HOME globally"
date: 2010-09-26
forum: General Help
---

### Post by omega psi on 2010-09-26
Hello, i need some help setting the JAVA_HOME to run services. I'm running Ubuntu 10.04 in VirualBox as guest on a Mac OS X - 10.6 host.

To be more precise, it seems be set, but artifactory complains. What i did so far, i edit the

[LIST=1]
[*]/etc/profile
[*]/etc/bash.bashrc
[/LIST]
to have JAVA_HOME globally accessible.```
JAVA_HOME=/usr/lib/jvm/java-6-sun/jre
export JAVA_HOME
PATH=$JAVA_HOME/bin:$PATH
```Running

[LIST=1]
[*]which java
[*]echo $JAVA_HOME
[/LIST]
will point to the right address, but running> service artifactory startas root i get> Created output file /opt/artifactory-2.2.5/logs/consoleout.log
Found JAVA= in JAVA_HOME=
Cannot find a JRE or JDK. Please set JAVA_HOME to a >=1.5 JRE


---

### Post by gmargo on 2010-09-26
Try editing the **/etc/environment** file.

---

### Post by omega psi on 2010-09-26
Thanx, i tried that. Caused that i wasn't able o login properly. Deleted my drive, reinstalled Ubuntu on VirtualBox and reinstalled java. Again, i edited /etc/environment```
JAVA_HOME=/usr/bin/java
export JAVA_HOME
PATH=$JAVA_HOME/bin:$PATH
```Same effect, can't login...

---

### Post by gmargo on 2010-09-26
It looks like you cannot use the $var format in the **/etc/environment** file. This **/etc/environment** worked for me on 10.04 Lucid (using the default .bashrc):
```

gmargo@lucid1:~$ cat /etc/environment
JAVA_HOME="/usr/lib/jvm/java-6-sun/jre"
PATH="/usr/lib/jvm/java-6-sun/jre/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"

gmargo@lucid1:~$ env | egrep "JAVA|^PATH"
PATH=/home/gmargo/bin:/usr/lib/jvm/java-6-sun/jre/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
JAVA_HOME=/usr/lib/jvm/java-6-sun/jre

```

---

### Post by omega psi on 2010-09-27
Thanx for the input so far. calling env will show, that JAVA_HOME is set properly. Now i have to checkout if i can get a java app to boot which relies on the JAVA_HOME to isolate the problem.

Thanx for the help!

---


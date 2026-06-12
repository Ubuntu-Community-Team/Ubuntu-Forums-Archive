---
title: "Oracle Java SE installation issues"
date: 2012-09-09
forum: General Help
---

### Post by ThrashManiac on 2012-09-09
I'm trying to install Oracle JavaSE (version 6u35, arch i586) on my Ubuntu 12.04 LTS amd64 system. 

*I use 32 java because I want to keep compatibility with existing applications.* 

This is what I do: 

[INDENT]0. //ubuntu amd64: install g++-multilib

1. # cp jdk-6u35-linux-i586.bin /opt/java/

2. # cd /opt/java/

3. # ./jdk-6u35-linux-i586.bin

4. # update-alternatives --install /usr/bin/java java /opt/java/jdk1.6.0_35/bin/java 100

5. # update-alternatives --install /usr/bin/javaws javaws /opt/java/jdk1.6.0_35/bin/javaws 100

6. # update-alternatives --install /usr/lib/mozilla/plugins/libjavaplugin.so libjavaplugin.so /opt/java/jdk1.6.0_35/jre/lib/i386/libnpjp2.so 100

7. # update-alternatives --config java

9. $ JAVA_HOME=/opt/java/jdk1.6.0_35/

10. $ export JAVA_HOME

11. $ PATH=$PATH:/opt/java/jdk1.6.0_35/bin

12. $ export PATH[/INDENT]

Result: 

[INDENT]a. Firefox doesn't "see" the java 

b. JAVA_HOME and PATH variables - they do not save their values -->> It's impossible to use javac in shell.[/INDENT] 

P.S. I also have tried setting up the environment variables under the root user - no effect.

---

### Post by ThrashManiac on 2012-09-09
I'm not sure, but I think that I've solved the problem, it should be: > 
update-alternatives --install /usr/**lib64**/mozilla/plugins/libjavaplugin.so libjavaplugin.so /opt/java/jdk1.6.0_35/jre/lib/i386/libnpjp2.so 100

...instead of: 
[QUOTE=ThrashManiac]
update-alternatives --install /usr/lib/mozilla/plugins/libjavaplugin.so libjavaplugin.so /opt/java/jdk1.6.0_35/jre/lib/i386/libnpjp2.so 100
[/QUOTE]
:guitar:

I'll try this one at home, and then, probably, close the topic. 

BTW, environment variables should be added to ~/.bashrc

Not tested, but I'm pretty sure that it will work...

---

### Post by ThrashManiac on 2012-09-09
> BTW, environment variables should be added to ~/.bashrc

Work ok. Not sure if this is "correct" way to set variables...

---


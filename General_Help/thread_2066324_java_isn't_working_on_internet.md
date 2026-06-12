---
title: "java isn't working on internet"
date: 2012-10-04
forum: General Help
---

### Post by X D face me on 2012-10-04
hey everyone

i've installed java using [this]("http://www.wikihow.com/Install-Oracle-Java-on-Ubuntu-Linux") guide. i've followed the guide just as it is and when i try the commands java -version and javac -version i get this: ```
java version "1.7.0_07"
Java(TM) SE Runtime Environment (build 1.7.0_07-b10)
Java HotSpot(TM) Server VM (build 23.3-b01, mixed mode)
```
 and this : ```
javac 1.7.0_07
```
 , but when i go to [the java site]("http://java.com/en/download/installed.jsp") it says that i don't have java installed, my java desktop appllications are working just fine and i can also develop java applications but websites that are using java aren't working for me, can anyone help?

this is my /etc/profile file

```

# /etc/profile: system-wide .profile file for the Bourne shell (sh(1))
# and Bourne compatible shells (bash(1), ksh(1), ash(1), ...).

if [ -d /etc/profile.d ]; then
  for i in /etc/profile.d/*.sh; do
    if [ -r $i ]; then
      . $i
    fi
  done
  unset i
fi

if [ "$PS1" ]; then
  if [ "$BASH" ]; then
    PS1='\u@\h:\w\$ '
    if [ -f /etc/bash.bashrc ]; then
	. /etc/bash.bashrc
    fi
  else
    if [ "`id -u`" -eq 0 ]; then
      PS1='# '
    else
      PS1='$ '
    fi
  fi
fi

umask 022
JAVA_HOME=/usr/local/java/jdk1.7.0_07
PATH=$PATH:$HOME/bin:$JAVA_HOME/bin
JAVA_HOME=/usr/local/java/jre1.7.0_07
PATH=$PATH:$HOME/bin:$JAVA_HOME/bin
export JAVA_HOME
export PATH=${PATH}:${HOME}/android-sdk-linux/tools:${HOME}/android-sdk-linux/platform-tools
```

---

### Post by QIII on 2012-10-04
1.  Those instructions are stupidly and insanely too complex for installing Oracle Java 7 on Ubuntu.  With "22 authors" you would think that one of them would have known that there is no need to remove OpenJDK and that it DOES NOT cause conflicts because you can choose between any number of Java versions that will coexist happily on a machine.  

2.  It doesn't look like those instructions do anything with the browser plugin if you happen to miss the rather unremarkable link that takes you to probably similarly ridiculous instructions, which is what you are lacking.

In the Java wiki in my signature, under "Oracle Java 7", "Command line methods" is a link "Using webupd8.org's strikingly simple method".

It will take care of downloading, installing, setting alternatives and setting up the browser plugin.  It will also make sure you have the latest updates as Oracle releases them without having to do anything more than your normal Ubuntu updates.

---

### Post by X D face me on 2012-10-04
really thanks for this, it truly helped me out.

p.s. where's the thanks button?

---


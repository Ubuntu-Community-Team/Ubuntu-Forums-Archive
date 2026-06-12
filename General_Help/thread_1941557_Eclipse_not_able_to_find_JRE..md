---
title: "Eclipse not able to find JRE."
date: 2012-03-15
forum: General Help
---

### Post by c2tarun on 2012-03-15
Hi friends.

I am trying to install sun java on my machine. As sun java is no longer in any repo I have to install it manually.
I downloaded the jdk tarball and copied it to /usr/local/java/jdk1.7.0_03
Then I added two environment variables in ~/.bashrc file
following is my ~/.bashrc file.

[HTML]# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).
if [ -f /etc/bash_completion ] && ! shopt -oq posix; then
    . /etc/bash_completion
fi

JAVA_HOME=/usr/local/java/jdk1.7.0_03
PATH=$JAVA_HOME/bin:$PATH[/HTML]

On running java -version on command prompt I am getting this:
[HTML]java version "1.7.0_03"
Java(TM) SE Runtime Environment (build 1.7.0_03-b04)
Java HotSpot(TM) 64-Bit Server VM (build 22.1-b02, mixed mode)
[/HTML]

On running 'which java' I am getting:
/usr/local/java/jdk1.7.0_03/bin/java


But When I am trying to run eclipse I am getting JRE not found error. How can I fix this??

---

### Post by Redeen on 2012-08-02
Had the same problem. This worked for me, but no promises:

sudo apt-get install openjdk-7-jre-headless

Eclipse (Helios) could then find JDK.

---


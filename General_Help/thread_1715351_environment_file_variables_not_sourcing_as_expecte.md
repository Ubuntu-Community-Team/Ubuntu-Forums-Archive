---
title: "environment file variables not sourcing as expected"
date: 2011-03-26
forum: General Help
---

### Post by theshowmecanuck on 2011-03-26
Hello,
    I added some env variables for java and maven to the /etc/environment file (from what I understand this is the correct place for system wide env variables, not the bashrc file). See the attached screen shot with the whole issue outlined as an example. Note that the paths contain symbolic links (e.g. JAVA_HOME and M2_HOME).

When the machine boots I can go to a command prompt and issue "java -version" and get a result as expected. 

When I issue "mvn --version" I get an unexpected result of the system telling me to try to install maven if I want to use it.

The paths to each are set up the same way in the environment file (I did have the path to the Maven executables set up differently but if you look I changed it to match exactly how the JAVA_HOME variable and path to bin is set up.

Now here is the really aggravatingly strange part:

If I source the file, i.e. 
"~$ source /etc/environment" 
things then work as expected (again see the attached screen shot). 

Can someone please tell me what I'm doing wrong or if there is a bug in the system? I'm not sure of which it is.

---

### Post by AlphaLexman on 2011-03-26
What are the read permissions of the '/etc/environment'?

---

### Post by theshowmecanuck on 2011-03-26
bill@muddy:/etc$ ll environment
-rw-r--r-- 1 root root 172 2011-03-26 19:47 environment

I have not changed the permissions. And this file is where the system stores the path variable for the base system. So the system can still do what it needs to with it.

As evidence, after booting, the environment successfully points to the java home bin directory allowing me to run the java executable. But as I said, the puzzling part is that does not successfully point to the maven bin directory so I cannot run the maven executable. That is, unless I explicitly 'source' the file. 

Since I can 'source' the file and have things then work, I don't see it as a permissions issue for myself either.

I would rather use variables since it makes upgrading development tools etc easier, but I will try explicitly adding the maven path to see if that works. But I would like to know what is up with this otherwise.

FWIW, here are the permissions of the directories in question in the /opt tree:

bill@muddy:/opt$ ll -d JAVA_HOME M2_HOME jdk1.6.0_24 apache-maven-3.0.3
drwxr-xr-x  6 root root 4096 2011-03-25 00:02 apache-maven-3.0.3/
lrwxrwxrwx  1 root root   11 2011-03-24 20:36 JAVA_HOME -> jdk1.6.0_24/
drwxr-xr-x 10 root root 4096 2011-03-24 20:35 jdk1.6.0_24/
lrwxrwxrwx  1 root root   18 2011-03-25 13:45 M2_HOME -> apache-maven-3.0.3/
bill@muddy:/opt$

---

### Post by theshowmecanuck on 2011-03-26
Interestingly when I do put in the verbatim path into the file it works as expected. Here is what it looks like now. 

bill@muddy:~$ cat /etc/environment
export JAVA_HOME="/opt/JAVA_HOME"
export M2_HOME="/opt/M2_HOME"

PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/opt/M2_HOME/bin:$JAVA_HOME/bin"
bill@muddy:~$ 


However, as I said, using variables is the better way to do it. I wonder what I'm doing wrong. <sigh>

---


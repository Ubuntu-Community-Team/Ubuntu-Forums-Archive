---
title: "Cannot change default JRE from 1.6 to 1.7"
date: 2012-05-17
forum: General Help
---

### Post by du7chm4n on 2012-05-17
I have several versions of JRE (Java Runtime Environment) in my system, 1.6 and 1.7. Version 1.6 is my current default JRE. Version 1.7 is from JDK 1.7.0 (tar.gz file) which I just installed it manually. Here is my installation step.


[LIST=1]
[*]Extract jdk1.7.0.tar.gz to /usr/local/jdk1.7.0.
[*]Set path by editing /etc/environment. here is the code.
[/LIST]
before,
```
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
```after,
```
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/jdk1.7.0/bin
```I rebooted my system, then I tested it by typing **javac** and **java** in terminal. They seem work correctly. But when I typed **java -version**, it showed version 1.6 instead 1.7. So, I figure it out by typing **which java**. It showed **/usr/bin/java** instead **/usr/local/jdk1.7.0/bin**. 



How can I change the old JRE (1.6) with new one (1.7)?


note:
1. I have tried this [tutorial]("https://mytechattempts.wordpress.com/2011/03/01/installing-java-manually-on-ubuntu/"). But it doesn't work at all.
2. I prefer **manuall installation** to **apt-get install **because I only have limited internet connection.

---

### Post by Canha on 2012-05-17
Instead of adding to the path set your alternatives.
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java) 
This page has some insight on it.

And I particularly like this method of installing it [http://askubuntu.com/questions/55848/how-do-i-install-oracle-java-jdk-7](http://askubuntu.com/questions/55848/how-do-i-install-oracle-java-jdk-7)

---

### Post by mutap on 2012-05-17
If you have 2 Java installations, you should update alternatives and set default Java version.
Syntax is something like this(check Google anyway, I'm not at Linux machine right now :))
sudo alternatives –install “usr/bin/java” “java” “/usr/<your_path>/jdk1.7.0_<your_version>/bin/java” 2
After that configure alternatives and set default version.

---

### Post by scouser73 on 2012-05-17
Please follow the advice set out on this site to install Java.

[[COLOR="Red"]**Easy Linux Tips - Java Install**[/COLOR]]("https://sites.google.com/site/easylinuxtipsproject/java")

I have used these instructions for updating Java and they work perfectly.

---

### Post by du7chm4n on 2012-05-17
> **scouser73 said:**
> Please follow the advice set out on this site to install Java.

[[COLOR=Red]**Easy Linux Tips - Java Install**[/COLOR]]("https://sites.google.com/site/easylinuxtipsproject/java")

I have used these instructions for updating Java and they work perfectly.

> **Canha said:**
> Instead of adding to the path set your alternatives.
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java) 
This page has some insight on it.

And I particularly like this method of installing it [http://askubuntu.com/questions/55848/how-do-i-install-oracle-java-jdk-7](http://askubuntu.com/questions/55848/how-do-i-install-oracle-java-jdk-7)

Thanks! those links work for me too!

[SOLVED]

---


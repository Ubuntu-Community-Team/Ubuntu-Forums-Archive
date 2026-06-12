---
title: "I tried to install Java, now I get: &quot;bash: /usr/bin/java: No such file or directory&quot;"
date: 2012-04-19
forum: General Help
---

### Post by purity89 on 2012-04-19
Since Canonical can no longer provide Java from Oracle, I'm following [this guide]("http://askubuntu.com/questions/56104/how-can-i-install-oracle-java-jre-7") (the highest rated answer) to install the latest Java from Oracle. I can't use OpenJDK/JRE.

After not getting Java to work after following the instructions (neither Firefox or Chrome had Java plugins, but the "java -version" did work), I tried reverting my changes, and I think I must have broken something, or deleted something I shouldn't have.

Here are some examples
```

:~$ java -version
bash: /usr/bin/java: No such file or directory
:~$ sudo update-alternatives --config java
There is only one alternative in link group java: /usr/lib/jvm/jre1.7.0/bin/java
Nothing to configure.

```

Does anyone know what I might have done, and what fixes it?

---

### Post by 2F4U on 2012-04-19
Did you try this answer from the site you posted?

> @Shoan, in that case, go to step "if only one alternative is shown then remember the number 0" 

If that doesn't work, there is a Ubuntu community documentation available:

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by purity89 on 2012-04-19
Yes, I tried that, but it didn't help. I don't see how this is related to my problems with "java -version" though..?

I get some kind of strange results when trying to configure Java though, not like the one in the instructions. This is probably related to just having one alternative though.
```

$ sudo update-alternatives --config java
There is only one alternative in link group java: /usr/lib/jvm/jre1.7.0 /bin/java
Nothing to configure.

```

The Ubuntu community documentation just links to the same instructions I'm using.

I tried doing what is suggested [here]("http://stackoverflow.com/questions/2165961/java-version-in-linux"), but "java -version" still doesn't work.

```

$ export PATH=$PATH:/usr/lib/jvm/jre1.7.0/bin
$ export JAVA_HOME=/usr/lib/jvm/jre1.7.0
$ java -version
bash: /usr/bin/java: No such file or directory

```


EDIT:
I'm trying to install JRE 6 now, using this method mentioned in the Community documentation (the repository method): [http://www.duinsoft.nl/packages.php?t=en#repo](http://www.duinsoft.nl/packages.php?t=en#repo)

EDIT2: **Installing JRE 6 using the above mentioned script-method worked. Now everything works perfectly!** I don't have JRE 7, but I don't think I need it either.

---

### Post by jerome1232 on 2012-04-19
I've installed java 7 following this guide, the only difference was I installed version 1.7.0_03 (the guide is for 1.7.0 ) and I had to change the paths to reflect that change.

[http://www.wikihow.com/Install-Oracle-Java-on-Ubuntu-Linux](http://www.wikihow.com/Install-Oracle-Java-on-Ubuntu-Linux)


Also if your machine is 64 bit I had to include a goofy workaround, I'm still not sure if this was specific to me running minecraft or not but here is the thread I made about it: [http://ubuntuforums.org/showthread.php?t=1956822](http://ubuntuforums.org/showthread.php?t=1956822)

The last post also shows what the end of my /etc/profile looked like.

---

### Post by purity89 on 2012-04-19
Thanks! I'll be sure to check that out if I ever get a need to install Java 7.

---


---
title: "why doesnt Java RTE in the repositories work with firefox?"
date: 2009-10-03
forum: General Help
---

### Post by eival on 2009-10-03
i installed it but its not loading when i view sites that use it, i was gonna try manually but none of the tutorials ive found actually get it to install.

can you please post the codes i need to install the java .bin file
[HTML]http://www.java.com/en/download/linux_manual.jsp?[/HTML]
 for Ubuntu 8.04.

thanks.:popcorn:

---

### Post by doas777 on 2009-10-03
you can install sun java with these instructions:
[http://www.cyberciti.biz/faq/howto-ubuntu-linux-install-configure-jdk-jre/](http://www.cyberciti.biz/faq/howto-ubuntu-linux-install-configure-jdk-jre/)

the reason java is not included by default and that it won't work with FF, is because the jre has some closed components that cannot be released as free software. the openjdk and icedtea projects attempt to free java, but they are not yet compatible with everything.

in the long run, java will be obsoleted and replaced before the complete sun implementation is foss licensable.

---

### Post by barbafant on 2009-10-04
> **doas777 said:**
> you can install sun java with these instructions:
[http://www.cyberciti.biz/faq/howto-ubuntu-linux-install-configure-jdk-jre/](http://www.cyberciti.biz/faq/howto-ubuntu-linux-install-configure-jdk-jre/)
I tried that and it doesn't work. That is, I did this:
$ sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-jdk
which seemed to work, and then I did this:
$ sudo update-java-alternatives -s java-6-sun
which seemed to work and then I tried to find and edit >  a file called /etc/jvm. This file defines the default system JVM search order. but I couldn't find it. I did find another file, etc/java-6-sun/jvm.cfg, but it didn't look like what the tutorial described so I left if alone.
I restarted Firefox and Java failed to work. I tried both a javatest at java.com and some java at facebook, which was what I wanted it for in the frst place.
I have previously installed xubuntu-rectricted-extras since it claimed to include Java. When that didn't work I followed the tutorial linked above.
I'm a bit flustered now and rather frustrated. Is there some diagnostic I can do that will point out what is missing, wrongly installed or has to be configured? And if so, how to do that? I am rather inexperienced so if you want to help me please explain step-by-step.
Help will be appreciated!

---

### Post by eival on 2009-10-05
wow, i actually checked the repositories again and further down the list of results from a "java" search, the official Sun plugin for firefox is there but it had a 1 star rating so i didnt see it when i first searched/installed Java:)

java apps in firefox now load properly

---


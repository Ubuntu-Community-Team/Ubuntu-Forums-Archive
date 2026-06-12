---
title: "Install Apache Tomcat 6"
date: 2010-03-19
forum: General Help
---

### Post by mosquetero on 2010-03-19
Hi everyone!

I have already downloaded Apache Tomcat 6 in a tar.gz. I am trying to follow the documentation of the Apache website but it is quite poor. I am having problems with 2 steps. MAybe someone is more experienced about this and can help me:

1st problematic step: Before running the script, the JAVA_HOME environment variable should be set to the base path of the JDK.

How can I do that? I have heard that this paths variable problem was just in Windows machines.

2nd problematic step: The documentation says I must do the following:

```
    cd $CATALINA_HOME/bin
    tar xvfz jsvc.tar.gz
    cd jsvc-src
    autoconf
    ./configure
    make
    cp jsvc ..
    cd ..

```

I must say that the file I have downloaded is not called jsvc.tar.gz but apache-tomcat-6.0.26.tar.gz but that's the only one I could find in the download webpage. Moving on to the problem, when I type the autoconf the terminal replies with: no input file.

Can you post me a link to a good documentation?

Thanks

---

### Post by mosquetero on 2010-03-19
I found good documentation and it works:

[http://www.howtogeek.com/howto/linux/installing-tomcat-6-on-ubuntu/](http://www.howtogeek.com/howto/linux/installing-tomcat-6-on-ubuntu/)

cheers

---


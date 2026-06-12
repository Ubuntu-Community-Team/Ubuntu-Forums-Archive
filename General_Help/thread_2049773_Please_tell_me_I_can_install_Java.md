---
title: "Please tell me I can install Java"
date: 2012-08-29
forum: General Help
---

### Post by Uikri on 2012-08-29
I always thought Ubuntu just came with Java, but now I see I was wrong. How can I install it? All I got from the site was a .tar.gz file, and I still have no idea how to work with those.

---

### Post by drmrgd on 2012-08-29
Have a look at this:

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

Under the Oracle Java 7 section, you'll find "Using webupd8.org's strikingly simple method", which is a great and simple way to get it set up in your system (thanks QIII!).

---

### Post by ajgreeny on 2012-08-29
You may also find that the openjdk-7-jre and the icedtea plugin works for all your requirements.  I have not used Sun (Oracle) java for many months, or perhaps years, and never have any problems at websites, or for the java apps and browser applets that I use.

Openjdk is in the normal repositories.

---

### Post by raja.genupula on 2012-08-29
i think you'd need this 
[http://askubuntu.com/questions/55848/how-do-i-install-oracle-java-jdk-7](http://askubuntu.com/questions/55848/how-do-i-install-oracle-java-jdk-7)

---

### Post by QIII on 2012-08-29
OpenJDK Is preferred in general because it is open source.

However, there is an exploit currently in the wild that exposes Java, including OpenJDK, to an "escape" exploit that can allow the execution of code outside of the Java sandbox in the user context.  Update 6 corrects this vulnerability.  The last I heard, OpenJDK has not caught up with this yet.

Use the "Using webupd8's strikingly simple method" in the wiki in my signature as suggested.  This will ensure that future updates from Oracle will be automatically installed as you do your normal Ubuntu updates.

Methods that include downloading and installing directly from Oracle require re-installation as Java is updated.  That means, in turn, that you must watch for them.

Even if you use Oracle Java 7 Update 6, be aware that yet another exploit has been discovered in the wild.  Although that exploit currently is targeted at Windows, it could easily be made to target Linux.

I expect a new Oracle Java 7 update in the near future, which is all the more reason to use a method that will automatically update your version without reinstallation.

---

### Post by claracc on 2012-08-30
I followed instructions in [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java) to install openjdk-7-jre and icedtea-7-plugin through synaptic in ubuntu 12.04.

As a result the java plugin in firefox appears as Icedtea-web 1.2 (1.2-2ubuntu1.1) which doesn't work with very simple applets pages, i.e.: [http://www.walter-fendt.de/ph14s/lever_s.htm](http://www.walter-fendt.de/ph14s/lever_s.htm)

However, the simple method of installing oracle java through ppa addressed by QIII install a working web java plugin to see applets.

Perhaps information in help.ubuntu.com about installing openjdk-7-jre and iced-7-plugin would have to be updated?

---

### Post by QIII on 2012-08-30
Some websites do not recognize OpenJDK as Java (despite the fact that it is the open source reference implementation), so it is not unusual for some applets not to work.

Incidentally, Oracle quietly released Oracle Java 7 Update 7 today to fix the horrible vulnerability today.

The webupd8 installer should update the version either immediately or in very short order.

---

### Post by claracc on 2012-08-31
I have just received this morning an update for openjdk-7-jre and icedtea-7 -plugin. Now it is recognized by firefox, its name is Icedtea-web plugin (using icedtea-web 1.2 (1.2-2ubuntu1.2)) and with it I can see web applets.

So this updated one icedtea plugin works, the 1.2-2ubuntu1.1 seems buggy.

---

### Post by dimas869 on 2012-09-02
hello, i am in Ubuntu Precise and have installed java-7-oracle which i got from webupd8team but when i use firefox browser it tells me that i need to update the java plugin "Java (TM) Plug-in 1.7.0_06" although when i get to Java page there is no update at all.

and Chromium does not ask for update, so is this a firefox problem?

---

### Post by Primefalcon on 2012-09-02
> **dimas869 said:**
> hello, i am in Ubuntu Precise and have installed java-7-oracle which i got from webupd8team but when i use firefox browser it tells me that i need to update the java plugin "Java (TM) Plug-in 1.7.0_06" although when i get to Java page there is no update at all.

and Chromium does not ask for update, so is this a firefox problem?
Sure you ca install the Java, I have...

just go to oracle and download the java package for your machine... and following the instructions provided on their site... 

One tip, put the extracted java in a version neutral name such as java_custom, that way to update it all you have to do is extract the new files to that folder in the future....

link is here btw: [http://java.com/en/download/linux_manual.jsp?locale=en](http://java.com/en/download/linux_manual.jsp?locale=en)

---

### Post by dimas869 on 2012-09-02
i dont think you properly read what i wrote...i did added a ppa from webupd8team and already installed

you know what...
i am going to fallow this instructions
[http://www.ubuntugeek.com/how-to-install-oracle-java-7-in-ubuntu-12-04.html](http://www.ubuntugeek.com/how-to-install-oracle-java-7-in-ubuntu-12-04.html)

thanks

---


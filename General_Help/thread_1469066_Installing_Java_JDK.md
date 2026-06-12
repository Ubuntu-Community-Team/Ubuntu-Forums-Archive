---
title: "Installing Java JDK"
date: 2010-05-01
forum: General Help
---

### Post by fterh on 2010-05-01
I found this article ([http://www.ubuntugeek.com/install-java-runtime-environment-jre-in-ubuntu-9-10-karmic.html](http://www.ubuntugeek.com/install-java-runtime-environment-jre-in-ubuntu-9-10-karmic.html)) which I thought was quite useful.

However I do not have the sun-java6-jdk package in my repository (Synaptic Package Manager). I'm going to try download direct from sun.com, but meanwhile if anybody has any idea how to get Java installed...

P/S: I need the JDK not JRE as I'll be trying to write some Android apps :D

---

### Post by 73ckn797 on 2010-05-01
Have you installed ubuntu-restricted-extras from Software Center or Synaptics?

---

### Post by QIII on 2010-05-01
If you are using Lucid, activate the partner repository.

```
add-apt-repository &#8220;deb http://archive.canonical.com/ lucid partner&#8221;
```and then add what you need from Synaptic.

Otherwise, for the JRE and the java plugin, check here:

[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

The JDK should be available as a stand-alone .tar file which you can extract and put wherever you want to.

In any case, be advised:  Any Java Update less than 20 contains serious security flaws and should not be used.

---

### Post by fterh on 2010-05-01
> **73ckn797 said:**
> Have you installed ubuntu-restricted-extras from Software Center or Synaptics?
Got it will give it a try.

> **QIII said:**
> If you are using Lucid, activate the partner repository.

```
add-apt-repository “deb http://archive.canonical.com/ lucid partner”
```and then add what you need from Synaptic.

Otherwise, for the JRE and the java plugin, check here:

[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

The JDK should be available as a stand-alone .tar file which you can extract and put wherever you want to.

In any case, be advised:  Any Java Update less than 20 contains serious security flaws and should not be used.
Okay thanks :)

---

### Post by fterh on 2010-05-01
I ran ```
sudo apt-get install ubuntu-restricted-extras
``` and it took quite a while, after it was done OpenJDK had been installed but it's not the latest (6b18) so I uninstalled ubuntu-restricted-extras. However uninstasllation was very fast, and after it was complete I realized that the Java was still on my system.

I had to open Synaptic and remove the OpenJDK & IcedTea. How do I install the latest 6b20 using Qlll's steps? :confused:

---

### Post by fterh on 2010-05-01
Bump! After reading post #3 I don't think I'd want to use anything other than 6b20. How do I get it installed?

---

### Post by QIII on 2010-05-02
If you are using Lucid, all the components can be installed from Synaptic after adding the partner repository.

If you are not running Lucid, go to the URL I provided to install most of Java components.  The instructions are step by step, and you can even cut and past the commands into the terminal

Then, to install the JDK, start here to download:

[http://java.sun.com/javase/downloads/widget/jdk6.jsp](http://java.sun.com/javase/downloads/widget/jdk6.jsp)

The instructions are here:

[http://java.sun.com/javase/6/webnotes/install/jdk/install-linux-64-self-extracting.html](http://java.sun.com/javase/6/webnotes/install/jdk/install-linux-64-self-extracting.html)

Just be sure to use the correct version number where the instructions say "<version>".

---


---
title: "problem with switch openJDK -&gt; Sun JDK"
date: 2009-11-02
forum: General Help
---

### Post by Dmitrey on 2009-11-02
hi all,
I have installed KUBUNTU 9.10 and (via synaptic) Sun JDK/JRE.
So I have
$ sudo update-java-alternatives --jre -l 
java-6-openjdk 1061 /usr/lib/jvm/java-6-openjdk 
java-6-sun 63 /usr/lib/jvm/java-6-sun 
 
However, when I perform 
$ sudo update-java-alternatives --jre -s java-6-sun 
I get
update-alternatives: error: no alternatives for pluginappletviewer. 

Any suggestions? 
Thank you in advance, D.

---

### Post by peculiar penguin on 2009-11-02
Do you have sun-java6-plugin installed?

---

### Post by Dmitrey on 2009-11-02
> **peculiar penguin said:**
> Do you have sun-java6-plugin installed?
yes

---

### Post by Dmitrey on 2009-11-10
The error message is no longer raised, I guess after some KUBUNTU patches installed.

---


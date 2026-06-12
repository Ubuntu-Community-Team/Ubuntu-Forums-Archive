---
title: "installing eclipse"
date: 2009-11-02
forum: General Help
---

### Post by Ubu-freak on 2009-11-02
After using vim to write all my java code I figured why not try out ecplise now so I was wondering how one would properly install and configure eclipse. I'm using karmic koala right now.

---

### Post by mthalis on 2009-11-02
Read this [http://www.h3manth.com/content/install-eclipse-galileo-35-ubuntu-karmic-910](http://www.h3manth.com/content/install-eclipse-galileo-35-ubuntu-karmic-910)

---

### Post by peculiar penguin on 2009-11-02
> **mthalis said:**
> Read this [http://www.h3manth.com/content/install-eclipse-galileo-35-ubuntu-karmic-910](http://www.h3manth.com/content/install-eclipse-galileo-35-ubuntu-karmic-910)

Synaptic shows Eclipse 3.5 being available in universe on my clean install here?

---

### Post by Martin_sensei on 2009-11-02
I got version 3.5 of Eclipse from the new Ubuntu Software Centre.

Just launch it from the Applications menu.

---

### Post by Ubu-freak on 2009-11-02
what should i set JAVA_HOME to? in 9.04 i don't remember setting it haha

---

### Post by Ubu-freak on 2009-11-02
also i don't think my eclipse supports.. cuz i go to windows->preferences and i can't find java

---

### Post by Mighty_Joe on 2009-11-02
> **Ubu-freak said:**
> also i don't think my eclipse supports.. cuz i go to windows->preferences and i can't find java

Which package did you install?  The Java Development Tools are in their own package: eclipse-jdt.

---

### Post by Ubu-freak on 2009-11-02
ok i'll give it a try
thx

---

### Post by Ubu-freak on 2009-11-02
> **Mighty_Joe said:**
> Which package did you install?  The Java Development Tools are in their own package: eclipse-jdt.
thx man it's working now

---

### Post by bmuluu on 2009-11-03
I did a clean install of Karmic and installed Eclipse.
I can't find the package for C Development tools.

eclipse-cdt is no longer available in my install options whenever I use apt-get., how can I install the C Development tools?

---

### Post by hazy on 2009-11-06
open the eclipse then in the "Help" menu select "Install New Software..." then from the list choose an address containing "cdt" something like this : ```
http://download.eclipse.org/tools/cdt/releases/galigeo
```
then click on the add button it will show you the available packages taht you can install

---

### Post by heepie on 2009-11-14
> **Ubu-freak said:**
> thx man it's working now

I'm having the same problem... what ecsacly did you do?

---

### Post by heepie on 2009-11-14
installing eclipse-jdt from synaptic solved the problem

---


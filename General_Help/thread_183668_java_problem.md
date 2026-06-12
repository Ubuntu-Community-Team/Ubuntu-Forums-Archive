---
title: "java problem"
date: 2006-05-28
forum: General Help
---

### Post by krcm on 2006-05-28
I have never had problems with java untill i tried to inbstall jalbum
it said i needed the vm, but when i try to install that it says it has unmet dependencies 
the dependencies seem to be classpath and classpath-common

when i install classpath first end then try to install jamvm, it can't install and says it can't uninstall classpath

???
](*,) 

Anyone out here please who understands this?

Thanks
An

---

### Post by meng on 2006-05-28
I'm not sure of the answer, but what do you get when you:

cat /etc/jvm

---

### Post by krcm on 2006-05-28
[QUOTE=krcm]I have never had problems with java untill i tried to inbstall jalbum
it said i needed the vm, but when i try to install that it says it has unmet dependencies 
the dependencies seem to be classpath and classpath-common

when i install classpath first end then try to install jamvm, it can't install and says it can't uninstall classpath

???
](*,) 

Anyone out here please who understands this?

Thanks
An[/QUOTE]
# This file defines the default system JVM search order. Each
# JVM should list their JAVA_HOME compatible directory in this file.
# The default system JVM is the first one available from top to
# bottom.

/usr/lib/jvm/java-gcj
/usr

An

---

### Post by krcm on 2006-05-28
[QUOTE=meng]I'm not sure of the answer, but what do you get when you:

cat /etc/jvm[/QUOTE]


# This file defines the default system JVM search order. Each
# JVM should list their JAVA_HOME compatible directory in this file.
# The default system JVM is the first one available from top to
# bottom.

/usr/lib/jvm/java-gcj
/usr


An

Sorry, the first answer went a bit wrong :-?

---

### Post by krcm on 2006-06-07
Could somebody please have another look at this?
I still can't install jalbum because it can't seem to find my java.
java is updated to the latest version.

thx
An

---

### Post by krcm on 2006-06-13
Seems that I would need jamvm to be able to install jalbum.
When i try to install jamvm through synaptic, i get the message that it has dependencies: classpath and classpath-common. 
When i say ok to install all of these progr, i get an error message that says that jamvm can't be installed becaus the other 2 aren't and can't be.

anybody an idea??

An

---


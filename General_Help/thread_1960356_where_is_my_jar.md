---
title: "where is my jar ?"
date: 2012-04-17
forum: General Help
---

### Post by winzip on 2012-04-17
i have installed openjdk-6-jdk.
I can see that by 
$java -version.
this prints :  java version 1.6.0_20 openjdk runtime environment.
But when i type.
$jar 
This does not find it. how do you fix it ?

---

### Post by sj1410 on 2012-04-17
there was a bug reported in some openjdk version with jar missing. either install fastjar or install java from [http://javadl.sun.com/webapps/download/AutoDL?BundleId=59621](http://javadl.sun.com/webapps/download/AutoDL?BundleId=59621)

---

### Post by winzip on 2012-04-17
> **sj1410 said:**
> there was a bug reported in some openjdk version with jar missing. either install fastjar or install java from [http://javadl.sun.com/webapps/download/AutoDL?BundleId=59621](http://javadl.sun.com/webapps/download/AutoDL?BundleId=59621)

I am worried. Are you saying to install another java ? i am using openjdk for jboss startup. New java might corrupt this settings.
What is fastjar ?

---


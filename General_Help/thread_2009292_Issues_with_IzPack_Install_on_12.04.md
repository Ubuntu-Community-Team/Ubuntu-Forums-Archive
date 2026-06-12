---
title: "Issues with IzPack Install on 12.04"
date: 2012-06-24
forum: General Help
---

### Post by ocryan on 2012-06-24
I just installed Ubuntu 12.04 on my computer and am trying to get IzPack  working correctly to no avail. I've installed IzPack just fine, but  setting the JAVA_HOME env variable is causing problems.

I installed the JDK (I need to compile  with IzPack), and am now trying to figure out which path is the correct  path for my JAVA_HOME variable.

In /usr/lib/jvm I have the following:
- java-1.6.0-openjdk-amd64
- java-6-openjdk-common
- java-6-openjdk-amd64
- java-7-openjdk-amd64

My question is, what is the difference between these and which one is suppose to be my JAVA_HOME?

Also, the IzPack website says I need to set the following variables as  well, if anyone could help me to find the correct paths for the  following that would be great. Thanks!
```

export JAVA_HOME=/usr/java/j2sdk1.4.2_06 
export JAVA_JAR=/usr/java/java_jar 
export JRE_HOME=/usr/java/j2sdk1.4.2_06/jre 
export CLASSPATH=/usr/java/j2sdk1.4.2_06/bin 
export PATH=/usr/java/j2sdk1.4.2_06/bin:/usr/java/j2sdk1.4.2_06/jre/bin:$PATH

```

---

### Post by ocryan on 2012-06-24
Tried to set the JAVA_HOME environment variable by adding the following in my bashrc file, using the below commands.

gedit ~/.bashrc

added the following with no change, still get the same error saying JAVA_HOME is not set.

JAVA_HOME=<your_path> 
export PATH=$PATH:$JAVA_HOME

The error I'm getting from IzPack when I try to compile is below.

.::  IzPack - Version 4.3.5 ::.
Warning: JAVA_HOME environment variable is not set.
  If build fails because sun.* classes could not be found
  you will need to set the JAVA_HOME environment variable
  to the installation directory of java.


Someone... please help me out. I've tried everything I've googled with no success.

---

### Post by ocryan on 2012-06-24
After several hours of attempting different fixes I googled to no avail, I found that the version of IzPack I'm using (**the latest non-beta, 4.3.5**) **incorrectly informs the user that JAVA_HOME is not set, when it actually is.**

  After completing my own XML file for a sample installation, it  compiled correctly and worked as expected. Obviously, I wanted to have  my JAVA_HOME correctly set before I began compiling, I didn't think to  try to go ahead and compile and see what happened, since IzPack was  continually telling me JAVA_HOME wasn't set and I assumed my  compilations wouldn't work because of that.


  **So, those of you who are getting this error after your  JAVA_HOME is set correctly when trying to compile, just ignore it and  continue, it should work correctly regardless of the error message.**

---


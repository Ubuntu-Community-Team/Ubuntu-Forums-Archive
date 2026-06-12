---
title: "Java Help"
date: 2011-10-09
forum: General Help
---

### Post by tyb97 on 2011-10-09
Hello, my problem is, I cannot seem to get Java 7 to work on ubuntu, I have gotten the .rpm, and converted it to .deb but it does not work, and I cannot get an eclipse version to install here either, the only option to down load is a tar.gz file, which I can do nothing with, and help?

---

### Post by mikejonesey on 2011-10-09
lol seems to be some confusion over java... you don't need to install java via a package just download a jdk from oracle, set the java home var to the jre inside and eclipse will open fine... if ur on 64bit arch remem to update the eclipse.ini java settings to match (will require a little for ram than the defaults...)

---

### Post by SavageWolf on 2011-10-09
Uh, you should install it from the Software Centre... Just open it and search for Java... You don't need to go to any websites or anything...

---

### Post by mikejonesey on 2011-10-09
@savage wolf;

yes sudo apt-get install java works with most;

i don;t see open java on the sys requirements page tho...
[http://www.eclipse.org/downloads/moreinfo/jre.php](http://www.eclipse.org/downloads/moreinfo/jre.php)

and from experience it does get buggy from time to time with eclipse... also if your developing webapps with eclipse the likleyhood is you'll want a oracle (not sun) jdk anyways...

no offence ment...

---

### Post by SavageWolf on 2011-10-09
... If you want the Sun Java things, see here:
[https://help.ubuntu.com/community/Java#Sun_Java](https://help.ubuntu.com/community/Java#Sun_Java)

Replace "lucid" with "natty" if you need to.

---

### Post by tyb97 on 2011-10-09
Thanks, but I already have JDK 6, I need 7, even when I install eclipse from the download center (Sorry I don't have the exact name) it auto installs JDK 6....

> **mikejonesey said:**
> lol seems to be some confusion over java... you don't need to install java via a package just download a jdk from oracle, set the java home var to the jre inside and eclipse will open fine... if ur on 64bit arch remem to update the eclipse.ini java settings to match (will require a little for ram than the defaults...)

What do you mean? how would I set the java home var.?

---

### Post by trozamon on 2011-10-09
why do you need 7? If you don't need it, just use 6 for now

---

### Post by tyb97 on 2011-10-09
A lot of features I use with my programs are for JDK 1.6.0_25+ which are not supported apparently..

---

### Post by trozamon on 2011-10-09
Ah, I understand you're need for 7 then. Hmmm... The only thing I can think of is either mess around with the tgz binaries or wait until it gets released on the repos. You're kinda gettin' screwed here.

---

### Post by sammiev on 2011-10-09
This might be what you want and it's the latest [Java]("http://sites.google.com/site/easylinuxtipsproject/java") version from JRE ( sun ). :)

---

### Post by Immolatus on 2011-10-09
I use the "self extracting binary" from sun's website. And don't forget to set the BASH path variable in .bashrc.

---

### Post by mikejonesey on 2011-10-10
sorry for late reply (was bed time in uk),

add
```
export JAVA_HOME="/usr/lib/sun/jdk1.5.0_22/jre"
```to the .bashrc or your profile to set the environment vatiable java home... this tells your progs where to look for the java... (most tomcat applications do this in the catalina.sh...)

(or to wherever you have extracted the jdk)

---

### Post by tyb97 on 2011-10-10
@sammiev, I could try that with JDK, I suppose it would work.

---


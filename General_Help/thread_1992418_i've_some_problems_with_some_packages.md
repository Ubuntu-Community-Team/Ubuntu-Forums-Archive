---
title: "i've some problems with some packages"
date: 2012-05-31
forum: General Help
---

### Post by Chicowolf on 2012-05-31
hi guys,
i'm following an how to at this link [http://arpandeb.com/03/2012/tech-guides/how-to-build-custom-rom-for-allwinner-a10-based-android-tablets-a-tutorial-and-guide.html](http://arpandeb.com/03/2012/tech-guides/how-to-build-custom-rom-for-allwinner-a10-based-android-tablets-a-tutorial-and-guide.html)
i'm at step 1 and 2, but i can't install those packages, the terminal says me an error, anyone can help me ?
sorry for my bad english

---

### Post by Cheesemill on 2012-05-31
What is the error message? You need to post exactly the commands you are trying and the error message you are getting for us to help.

---

### Post by sammiev on 2012-05-31
Interesting as it wants to install into java. I can see a few other errors coming if they do not use sun-java and version 6 when java 7 is much the standard now I would think. Looking on. :)

---

### Post by VeeDubb on 2012-05-31
The first problem is that the first 2 steps are to install Sun Java 6.

Sun Java is no longer available through any of the major Ubuntu repos, and as sammiev pointed out, it has been replaced by Java 7 anyway.  

You can try skipping any package that is directly related to with Sun Java and see if it will work with OpenJDK, which 80-90% of things seem to, or you can set about installing Sun Java.  There are numerous how-to's out there, but almost all of them are grossly outdated.  I ended up using a repo from webup8team, and that seems to have done the trick.

---

### Post by Cheesemill on 2012-05-31
> **VeeDubb said:**
> The first problem is that the first 2 steps are to install Sun Java 6.

Sun Java is no longer available through any of the major Ubuntu repos, and as sammiev pointed out, it has been replaced by Java 7 anyway. 
This isn't a problem. Step 1 is telling you how to install Java 6 from a PPA, not from the standard repos.

---

### Post by Chicowolf on 2012-06-01
so i can install open jdk ?
another question, when i type 
```
sudo apt-get install git-core gnupg flex bison gperf build-essential zip curl zlib1g-dev libc6-dev lib32ncurses5-dev ia32-libs x11proto-core-dev libx11-dev lib32readline5-dev lib32z-dev libgl1-mesa-dev g++-multilib mingw32 tofrodos python-markdown libxml2-utils xsltproc



```
terminal show me the same error. what can i do ?

---

### Post by Cheesemill on 2012-06-01
> **Chicowolf said:**
> so i can install open jdk ?
another question, when i type 
```
sudo apt-get install git-core gnupg flex bison gperf build-essential zip curl zlib1g-dev libc6-dev lib32ncurses5-dev ia32-libs x11proto-core-dev libx11-dev lib32readline5-dev lib32z-dev libgl1-mesa-dev g++-multilib mingw32 tofrodos python-markdown libxml2-utils xsltproc



```terminal show me the same error. what can i do ?

Again, you haven't told us what the error is. Without it we can't help.

---

### Post by Chicowolf on 2012-06-01
```
Reading package lists ... done
 Building dependency tree
 Reading state information ... done
 The lib32ncurses5-dev package is not available, but is referred to by another
 package. This may mean that the package is missing, obsolete
 or is only available from another source

 The package ia32-libs is not available, but is referred to by another
 package. This may mean that the package is missing, obsolete
 or is only available from another source

 E: The package "lib32ncurses5-dev" has no installation candidate
 E: The package "ia32-libs" has no installation candidate
 E: Could not find package lib32readline5-dev
 E: Could not find package lib32z-dev
```
the source is in italian :D i translate it :)
but i've another problem !!!
update manager tries to install sun java jdk 7, but fails. Yesterday I did various tests to install java 6, and maybe I made a mess :D

---


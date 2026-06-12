---
title: "java problem"
date: 2009-11-15
forum: General Help
---

### Post by recycledhippy on 2009-11-15
I've updated to Ubuntu 9.10 and now need to update java but I am having a problem. when I try this 
 sudo apt-get install sun-java6-jre sun-java6-jdk sun-java6-plugin  
I get this

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  sun-java6-jdk: Depends: sun-java6-bin (= 6-15-1) but 6-16-0ubuntu1.9.04 is to be installed
  sun-java6-plugin: Depends: sun-java6-bin (= 6-15-1) but 6-16-0ubuntu1.9.04 is to be installed
E: Broken packages
 any help would be great!!!

---

### Post by scouser73 on 2009-11-15
I've found this tutorial to be a really good way to install Sun Java [[COLOR="Red"]**Here**[/COLOR]]("http://sites.google.com/site/easylinuxtipsproject/java")

It tells you how to install Java for both 32 & 64 bit systems.

Although on the site it states that it's only for Ubuntu 9.10, I have installed it on Ubuntu 9.04 and it works flawlessly.

---

### Post by recycledhippy on 2009-11-15
thanks that got it working!!!

---


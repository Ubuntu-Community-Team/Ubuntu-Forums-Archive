---
title: "How to get Sun Java?"
date: 2011-10-17
forum: General Help
---

### Post by Cam! on 2011-10-17
I just installed Ubuntu 11.10, and I'm confused as to how to download the latest version of Sun Java. How do I go about doing so?

---

### Post by Gyokuro on 2011-10-17
To install the jdk6 you have to enter:

# for java development 
sudo apt-get install sun-java6-jdk 

# for only running java apps.
sudo apt-get install sun-java6-jre

-HTH

---

### Post by Cam! on 2011-10-17
I'm having a problem. When entering that into the terminal, I get a "Package ________ has no installation candidate" error.

---

### Post by Pjotr123 on 2011-10-17
Oracle (Sun) Java JRE has been removed from the repositories of Ubuntu 11.10. You can still install it by applying this how-to: [http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

Good luck! :-)

---


---
title: "How do I download Java for Ubuntu?"
date: 2011-12-08
forum: General Help
---

### Post by The Linux Newb on 2011-12-08
I installed Ubuntu on my PC yesterday, and I've never used any type of Linux before then, I'm completely new to this. 

I'm wondering how to install Java (JRE) on ubuntu  

I googled it to figure out how but it wasn't working.

if it matters, my installation of Ubuntu is Ubuntu 11.10 64-bit 

thanks, sorry if this is a really stupid question, I'm a Windows user, and I'm not used to the way stuff is installed on Linux operating systems.

---

### Post by BC59 on 2011-12-08
Go to the dash (upper circle icon in left bar-launcher) push it and to the search box right--**Ubuntu Software Center**. The icon appears you push it and from the application search box, write **Ubuntu restricted**. Install them and inside is included Java and many other useful things.

---

### Post by BC59 on 2011-12-08
Other options:

To install OpenJDK run on a terminal CTRL+ALT+T:
```
sudo apt-get install openjdk-7-jre
```

To install Oracle (previously Sun) Java 6 from:
```
sudo add-apt-repository ppa:ferramroberto/java
sudo apt-get update
sudo apt-get install sun-java6-jdk sun-java6-plugin
```

And if you want to install Oracle Java 7:

[http://www.webupd8.org/2011/09/how-to-install-oracle-java-7-jdk-in.html](http://www.webupd8.org/2011/09/how-to-install-oracle-java-7-jdk-in.html)

---

### Post by jim_deadlock on 2011-12-08
They removed Java JRE from the regular repositories in recent months, it is rather annoying it has to be said. The repository posted by BC59 will give you Java version 6 update 26 and there is no sign of it getting updated any time soon. 6-26 is supposed to be insecure, so if you want the latest secure version 6-29 you'll have to install it manually, I found this page very good:

[Oracle (Sun) Java JRE for Ubuntu, Linux Mint and Debian]("http://sites.google.com/site/easylinuxtipsproject/java#TOC-Oracle-Sun-Java:-removed-from-all-r")

---

### Post by The Linux Newb on 2011-12-08
> **jim_deadlock said:**
> They removed Java JRE from the regular repositories in recent months, it is rather annoying it has to be said. The repository posted by BC59 will give you Java version 6 update 26 and there is no sign of it getting updated any time soon. 6-26 is supposed to be insecure, so if you want the latest secure version 6-29 you'll have to install it manually, I found this page very good:

[Oracle (Sun) Java JRE for Ubuntu, Linux Mint and Debian]("http://sites.google.com/site/easylinuxtipsproject/java#TOC-Oracle-Sun-Java:-removed-from-all-r")

That worked perfectly, thanks ! :)

---


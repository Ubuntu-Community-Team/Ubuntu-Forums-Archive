---
title: "Java 64-bit Runtime?"
date: 2011-10-03
forum: General Help
---

### Post by MagnetsNextToMotherboard on 2011-10-03
How do I install this Java to my 64-bit Ubuntu system? I downloaded the "Linux x64" one because I specifically want the 64-bit version, so I can use more than 4GB of RAM on it.

Thanks.

---

### Post by MagnetsNextToMotherboard on 2011-10-03
[http://java.com/en/download/manual.jsp?locale=en](http://java.com/en/download/manual.jsp?locale=en) This is where I downloaded it.

---

### Post by angryfirelord on 2011-10-03
Java is included in the repositories, so there's no need to download it from Oracle. You have two choices:

sun-java6-jdk for the JDK
sun-java6-jre for just the runtime environment.

---

### Post by MagnetsNextToMotherboard on 2011-10-03
But is it the 64-bit version?

---

### Post by sum1nil on 2011-10-03
The 64bit version I downloaded is (although just the jre) was 'jre-6u27-linux-x64.bin'. I think I had to 'sudo chmod u+x jre-6u27-linux-x64.bin'  to make it executable. Then in the directory the file resides: ./jre-6u27-linux-x64.bin to install. 
Do not forget to export it in you <home>/.profile by adding a  line at the bottom: export PATH=/usr/local/jre1.6.0_27/bin:$PATH (which will be different for the JDK).

I do not think that the package manager for Ubuntu has a listing for the 64bit version.

Good luck.
:popcorn:

---

### Post by MagnetsNextToMotherboard on 2011-10-03
I don't understand the terminal codes at all yet, what I want is just the full version of Java in 64-bit.

---

### Post by MagnetsNextToMotherboard on 2011-10-03
):P Can anyone tell me how I can get Java 64-bit Runtime? I specifically need 64-bit, so that I can run applications that require more than 4GB of RAM like Minecraft. Thanks.

Here's the list that I found, it has Java 64-bit for linux but I have no idea how to install it. [http://java.com/en/download/manual.jsp?locale=en](http://java.com/en/download/manual.jsp?locale=en)

---

### Post by oldos2er on 2011-10-04
[https://sites.google.com/site/easylinuxtipsproject/java](https://sites.google.com/site/easylinuxtipsproject/java)

---

### Post by oldos2er on 2011-10-04
Threads merged. Please don't open more than one thread per topic.

---


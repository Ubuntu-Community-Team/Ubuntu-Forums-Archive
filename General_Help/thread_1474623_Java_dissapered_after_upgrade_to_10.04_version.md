---
title: "Java dissapered after upgrade to 10.04 version"
date: 2010-05-06
forum: General Help
---

### Post by Lavix on 2010-05-06
I had Ubuntu KArmic Koala with Java sun-sdk  6 installed and everything worked fine. After Upgrade to 10.04 via Update Manager  - no java detected...
When I type in

java -version

I get:

The program 'java' can be found in the following packages:
 * gcj-4.4-jre-headless
 * openjdk-6-jre-headless
 * cacao
 * gij-4.3
 * jamvm

 How is it possible to resolve this problem, please? Even if try to install it from Synaptic Package Manager, it doen't work. Please help. Thanks

---

### Post by progre55_icky on 2010-05-06
Lucid has java openjdk as its "official" java now. If you want sun's java, you need to uncomment the "partner" PPAs in /etc/apt/sources.list
Hope you know the rest.. Just update (sudo apt-get update) and install (sudo apt-get install sun-java6-jdk (or sun-java6-jre)).

Cheers,
progre55

---

### Post by Lavix on 2010-05-06
Yeah, thank you for your rapid response. After googling a little, I discovered what exactly you explained. So I just selected open jdk in Synaptic Manager and now everything works as before but not Netbeaans that I used for Ruby on Rails. I'll be searchin why.

---

### Post by Lavix on 2010-05-06
I had to install a new version of Netbeans because the old one based on older sun jdk didn't see it. Now Eclipse and Netbeans wok fine both.

Thanks.

---


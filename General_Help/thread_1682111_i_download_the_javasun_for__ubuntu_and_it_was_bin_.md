---
title: "i download the javasun for  ubuntu and it was bin file"
date: 2011-02-05
forum: General Help
---

### Post by jolian ramos on 2011-02-05
how to install Javasun for ubuntu please help me ?

---

### Post by DougieFresh4U on 2011-02-05
You should be able to install it from 'Ubuntu Software Center' if you have all the repo's enabled.
What Ubuntu are you using?

---

### Post by jolian ramos on 2011-02-05
ubuntu 10.04

---

### Post by howefield on 2011-02-05
I think it is version 6.22 that is in the repositories, certainly for 10.10 it is. That's the easy way to get Sun Java, install sun-java6-jre sun-java6-fonts and sun-java6-plugin

If you want or must have the latest which is version 6.23, follow the guide here...

[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

---

### Post by jolian ramos on 2011-02-05
i use ubuntu 10.04
> **DougieFresh4U said:**
> You should be able to install it from 'Ubuntu Software Center' if you have all the repo's enabled.
What Ubuntu are you using?

---

### Post by jolian ramos on 2011-02-05
i don't understand what repositories you are talking about i am pure beginner in ubuntu so please explain more thanks 

> **howefield said:**
> I think it is version 6.22 that is in the repositories, certainly for 10.10 it is. That's the easy way to get Sun Java, install sun-java6-jre sun-java6-fonts and sun-java6-plugin

If you want or must have the latest which is version 6.23, follow the guide here...

[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

---

### Post by jolian ramos on 2011-02-05
anyway i checked the link and i already knew how to install it 
thank you 

> **howefield said:**
> I think it is version 6.22 that is in the repositories, certainly for 10.10 it is. That's the easy way to get Sun Java, install sun-java6-jre sun-java6-fonts and sun-java6-plugin

If you want or must have the latest which is version 6.23, follow the guide here...

[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

---

### Post by dBuster on 2011-02-06
> **howefield said:**
> I think it is version 6.22 that is in the repositories, certainly for 10.10 it is. That's the easy way to get Sun Java, install sun-java6-jre sun-java6-fonts and sun-java6-plugin

If you want or must have the latest which is version 6.23, follow the guide here...

[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

Okay so a while back I followed the steps on the quoted page to update my java and ever since I have not been able to play any java based website games.  Java tests out just fine with ver 6 update 23 but still no games.  

One think I think is an issue is that I can not for the life of me get the jdk to install.  Not sure if that makes a load of anything for the game websites, ie pogo, yahoo games, etc.  Here is some output information and what I get told from when I try to install the jdk.

```
david@david-laptop:~$ java -version
java version "1.6.0_22"
Java(TM) SE Runtime Environment (build 1.6.0_22-b04)
Java HotSpot(TM) 64-Bit Server VM (build 17.1-b03, mixed mode)
david@david-laptop:~$ sudo apt-get install sun-java6-jdk
[sudo] password for david: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  sun-java6-jdk: Depends: sun-java6-bin (= 6-13-1) but 6.22-0ubuntu1~9.04.1 is to be installed
E: Broken packages

```

I know I am running 9.04 but shortly I am going to update to 10.04.1 but in the meantime I would love to play the occasional game or two.  Not to mention I bet this might fix my facebook photo uploader and so forth...

---

